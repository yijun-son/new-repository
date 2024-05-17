//7-1, 7-2
#include <iostream>
#include <string>
using namespace std;

class Book {
	string title;
	int price;
	int pages;
public:
	Book(string title = "", int price = 0, int pages = 0) {
		this->title = title; this->price = price; 	this->pages = pages;
	}
	void show() {
		cout << title << ' ' << price << " Won " << pages << " Pages" << endl;
	}
	string getTitle() { return title; }
	Book& operator +=(int price);		//P7.1(1)
	Book& operator -=(int price);		//P7.1(1)
	bool operator ==(int price);		//P7.1(1) 
	bool operator ==(string title);		//P7.2(1)
	bool operator ==(Book book);		//P7.2(1)
};

Book& Book::operator +=(int price) {
	this->price += price;
	return *this;
}

Book& Book::operator -=(int price) {
	this->price -= price;
	return *this;
}

bool Book::operator ==(int price) {
	if (this->price == price) return true;
	else return false;
}

bool Book::operator ==(string title) {
	if (this->title == title) return true;
	else return false;
}

bool Book::operator ==(Book book) {
	if (this->title == book.title &&
		this->price == book.price &&
		this->pages == book.pages) return true;
	else return false;
}


int main() {
	Book a("YOUTH", 20000, 300), b("FUTURE", 30000, 500);
	a += 500; // Increase the price of the book a by 500 Won
	b -= 500; // Decrease the price of the book b by 500 Won
	a.show();
	b.show();
	cout << "---P7.1(1)----------------------------------------------" << endl;

	Book mp("Masterpiece C++", 30000, 500), hq("High Quality C++", 30000, 500);
	if (mp == 30000) cout << "Price is 30000 Won" << endl;	// price comparison
	if (mp == "Masterpiece C++") cout << "This book is the Masterpiece C++." << endl; 	// Comparison of book title
	if (mp == hq) cout << "These are some books." << endl; 					// Comparison of title, price & pages 
	cout << "---P7.2(1)----------------------------------------------" << endl;

}
