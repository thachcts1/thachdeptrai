#include <iostream>
#include <vector>
#include <string>

using namespace std;

/* ===== Trang thai cong viec ===== */
enum Status {
    DANG_LAM = 1,
    HOAN_THANH,
    KHONG_HOAN_THANH
};

/* ===== Lop Work ===== */
class Work {
private:
    int id;                 // ma cong viec
    string content;         // noi dung cong viec
    int hours;              // so gio thuc hien
    string createDate;      // ngay tao
    Status status;          // trang thai

public:
    // Ham tao
    Work(int _id, string _content, int _hours, string _date) {
        id = _id;
        content = _content;
        hours = _hours;
        createDate = _date;
        status = DANG_LAM; // mac dinh
    }

    // Getter
    int getId() {
        return id;
    }

    Status getStatus() {
        return status;
    }

    // Setter
    void setContent(string newContent) {
        content = newContent;
    }

    void setStatus(Status newStatus) {
        status = newStatus;
    }

    // Hien thi thong tin cong viec
    void display() {
        cout << "ID: " << id
             << " | Noi dung: " << content
             << " | Gio: " << hours
             << " | Ngay tao: " << createDate
             << " | Trang thai: ";

        if (status == DANG_LAM)
            cout << "Dang lam";
        else if (status == HOAN_THANH)
            cout << "Hoan thanh";
        else
            cout << "Khong hoan thanh";

        cout << endl;
    }
};

/* ===== Lop WorkManager ===== */
class WorkManager {
private:
    vector<Work> works;   // danh sach cong viec
    int autoId = 1;       // ma cong viec tu tang

public:
    // Hien thi danh sach
    void showAll() {
        if (works.empty()) {
            cout << "Danh sach cong viec rong!\n";
            return;
        }

        for (int i = 0; i < works.size(); i++) {
            works[i].display();
        }
    }

    // Them cong viec
    void addWork() {
        string content, date;
        int hours;

        cin.ignore();
        cout << "Nhap noi dung cong viec: ";
        getline(cin, content);

        cout << "Nhap so gio can thuc hien: ";
        cin >> hours;

        cin.ignore();
        cout << "Nhap ngay tao (dd/MM/yyyy): ";
        getline(cin, date);

        Work w(autoId, content, hours, date);
        works.push_back(w);
        autoId++;

        cout << "Them cong viec thanh cong!\n";
    }

    // Cap nhat noi dung
    void updateContent() {
        int id;
        cout << "Nhap ma cong viec: ";
        cin >> id;

        for (int i = 0; i < works.size(); i++) {
            if (works[i].getId() == id) {
                cin.ignore();
                string newContent;
                cout << "Nhap noi dung moi: ";
                getline(cin, newContent);
                works[i].setContent(newContent);
                cout << "Cap nhat thanh cong!\n";
                return;
            }
        }

        cout << "Khong tim thay cong viec!\n";
    }

    // Chuyen trang thai
    void changeStatus() {
        int id;
        cout << "Nhap ma cong viec: ";
        cin >> id;

        for (int i = 0; i < works.size(); i++) {
            if (works[i].getId() == id) {

                if (works[i].getStatus() != DANG_LAM) {
                    cout << "Chi duoc doi trang thai khi Dang lam!\n";
                    return;
                }

                int choice;
                cout << "1. Hoan thanh\n2. Khong hoan thanh\nChon: ";
                cin >> choice;

                if (choice == 1)
                    works[i].setStatus(HOAN_THANH);
                else if (choice == 2)
                    works[i].setStatus(KHONG_HOAN_THANH);
                else {
                    cout << "Lua chon khong hop le!\n";
                    return;
                }

                cout << "Doi trang thai thanh cong!\n";
                return;
            }
        }

        cout << "Khong tim thay cong viec!\n";
    }

    // Loc cong viec theo trang thai
    void filterByStatus() {
        int choice;
        cout << "1. Dang lam\n2. Hoan thanh\n3. Khong hoan thanh\nChon: ";
        cin >> choice;

        for (int i = 0; i < works.size(); i++) {
            if (works[i].getStatus() == choice) {
                works[i].display();
            }
        }
    }
};

/* ===== MAIN ===== */
int main() {
    WorkManager manager;
    int choice;

    do {
        cout << "\n-------- MENU --------\n";
        cout << "1. Hien thi danh sach\n";
        cout << "2. Them cong viec\n";
        cout << "3. Cap nhat noi dung\n";
        cout << "4. Chuyen trang thai\n";
        cout << "5. Loc theo trang thai\n";
        cout << "6. Thoat\n";
        cout << "Chon: ";
        cin >> choice;

        switch (choice) {
        case 1:
            manager.showAll();
            break;
        case 2:
            manager.addWork();
            break;
        case 3:
            manager.updateContent();
            break;
        case 4:
            manager.changeStatus();
            break;
        case 5:
            manager.filterByStatus();
            break;
        case 6:
            cout << "Thoat chuong trinh!\n";
            break;
        default:
            cout << "Lua chon sai!\n";
        }
    } while (choice != 6);

    return 0;
}
