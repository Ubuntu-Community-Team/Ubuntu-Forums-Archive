---
title: "c++ exe help"
date: 2008-03-15
forum: General Help
---

### Post by Flynn555 on 2008-03-15
hi.  im sort of new to programing in ubuntu. (been usin unix)
i wrote a hello world test to see if i could compile and run in ubuntu.
im using the compiler g++ to make the a.out
but whenever i execute the a.out i get this...

bash: a.out: command not found

ive tried naming the exe something else and it still doesnt work

script:

chad@chad-desktop:~/Documents$ cat program.cc
//helo world test to see if i can do c++ on my computer

#include <iostream>
using namespace std;

int main()
{
  cout << "hello world" << endl;

  return 0;
}
chad@chad-desktop:~/Documents$ g++ program.cc
chad@chad-desktop:~/Documents$ ls
a.out                            ostux-usplash
ebooks                           program.cc
greasemonkey user scripts        program.cc~
linux                            school

chad@chad-desktop:~/Documents$ a.out
bash: a.out: command not found

---

### Post by taurus on 2008-03-15
Try

```
./a.out
```

The reason you have to include ./ is that ~/Documents is not in your path.

---

### Post by Steveway on 2008-03-15
Use ./a.out
and don't forget to give it executable permissions.
And it's not a "exe" it's an executable program, "exe"-files are for Windows.
EDIT: A few seconds too late.

---

### Post by Flynn555 on 2008-03-15
thanks  worked :D

also i know in unix if i were to type
    nedit program.cc &  
as compared to just
   nedit program.cc

it would keep me from closing the text editor if i wanted to type something in term.  is there something similar to the "&" in linux

---

### Post by bruce89 on 2008-03-15
You ought to use
```
g++ -o prog_name prog_source.cpp
```
as compiling different programs will yield seperate executables this way, as opposed to overwriting *a.out* all the time.

---

### Post by koenn on 2008-03-15
& exists on linux too, it puts a process in the background, so you return to a command prompt while the program keeps running? Is that what you want ?

---

