---
title: "I can't find missing semicolon"
date: 2024-11-22
forum: General Help
---

### Post by Acharn on 2024-11-22
It's been twenty years since I wrote C programs, and recently I've been trying to start learning C++ from Bjarne Stroustrup's Programming and Principles. I'm running ubuntu 24.04 LST, which had GCC 13.0.2, which has C++ 17 built-in, but eventually I was able to find the support material which allows me to run C++ 23 code (which is what Stroustrup uses). I was able to compile the "hello, world" program, but the second program is driving me crazy. I've had missing semicolons, lots of them, but in this case I can't figure out what the compiler is complaining about.
```

// read and write a first name
#include "PPPheaders.h"

int main ()
    {
  cout << "Please enter your first name (followed by \"enter\"):\n";
  string first_name;
  cin >> first_name;
  cout << "Hello, " first_name "!\n";
    }

```
The compiler insists I'm missing a semi-colon
```

roger@henry:~/Projects$ g++ -std=c++2b first_name.cpp
first_name.cpp: In function ‘int main()’:
first_name.cpp:9:20: error: expected ‘;’ before ‘first_name’
    9 |   cout << "Hello, " first_name "!\n";

```
I don't know what besides a missing semicolon would throw this error. Can anyone help me?

---

### Post by TheFu on 2024-11-22
Is "string" a known struct/class/keyword?

You know that nobody actually uses cin/cout ... er ... ever after the 1 day of class.

I'd expect 
```
#include <print>
...
std::println("");
```
to be used in a first program.

Or ... if you must use iostream
```
#include <iostream>
int main() {
    std::cout << "Hello World\n"; 
}
```
* stolen from [https://www.modernescpp.com/index.php/c23-a-modularized-standard-library-stdprint-and-stdprintln/](https://www.modernescpp.com/index.php/c23-a-modularized-standard-library-stdprint-and-stdprintln/)

---

### Post by Holger_Gehrke on 2024-11-22
I could be completely wrong (not a C++ programmer ...), but I'd expect something between all those things you send to standard output probably whatever operator is used in C++ for concatenating strings. After a quick look at some examples online, I believe that a couple of additional '<<' might be what you need ('cout << "Hello, " << first_name << "!\n";')

Holger

---

### Post by TheFu on 2024-11-22
```
main.cpp:7:25: error: expected &#8216;;&#8217; before &#8216;first_name&#8217;
    7 |   std::cout << "Hello, " first_name "!\n";
      |                         ^~~~~~~~~~~

```
So, you need 
```
std::cout << "Hello, " [COLOR="#FF0000"]<<[/COLOR] first_name[COLOR="#FF0000"] << [/COLOR] "!\n";
```
as HG says.

---

### Post by Tadaen_Sylvermane on 2024-11-22
```
"Hello, " first_name "!\n";
```

You've got double quotes inside double quotes. so it's quoting hello and "!\n" respectively, ignoring your first name. I'm not familiar with c++ directly but in C that line would be written as such

```
printf("Hello, %s!\n", first_name);
```

TheFu nailed it.

Formatting is everything.

---

### Post by Tadaen_Sylvermane on 2024-11-22
*double post*

---

### Post by Acharn on 2024-11-22
Holger, I think that's it. I copied exactly from the textbook, but I have a vague memory from other books that those operators were used. Yes, adding those makes it compile perfectly. Since I don't believe Bjarne Stroustrup made a mistake, C++ 23 must have changed a lot from C++ 20. Thank you so much.

---

