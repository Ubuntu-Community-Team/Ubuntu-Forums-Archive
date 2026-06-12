---
title: "c++ sources won't compile"
date: 2008-02-13
forum: General Help
---

### Post by natirips on 2008-02-13
Ok, I made a program as simple as it could be:
```
int main(){return 0;}

```Then I go to console and:```
natirips@natirips-laptop:~/c$ cc test.cpp 
cc: error trying to exec 'cc1plus': execvp: Nema takve datoteke ili direktorija
natirips@natirips-laptop:~/c$
```
It's the same with all c++ programs I tried to compile, while c sources compile flawlessly...

Am I doing something wrong or what?
P.S.: "Nema takve datoteke ili direktorija" literally translates to "So such file or directory".

---

### Post by thecorleonefamily on 2008-02-13
I don't know whether this will be helpful since I am new myself to Linux.

First you need g++

Open terminal and type:

sudo apt-get install g++

Install g++.

After that save the C++ file with .cc extension.

Then browse to the directory where the C++ file is and type:

g++ <filename.cc> -o <outputfilename>

It should work. Make sure you use the newer C++ format:

like:

#include <iostream>
using namespace std;

int main()

{

return 0;

}

Sorry if it doesn't help! It should :)

---

### Post by natirips on 2008-02-13
It works now, thanks.

---

### Post by stchman on 2008-02-13
> **natirips said:**
> Ok, I made a program as simple as it could be:
```
int main(){return 0;}

```Then I go to console and:```
natirips@natirips-laptop:~/c$ cc test.cpp 
cc: error trying to exec 'cc1plus': execvp: Nema takve datoteke ili direktorija
natirips@natirips-laptop:~/c$
```
It's the same with all c++ programs I tried to compile, while c sources compile flawlessly...

Am I doing something wrong or what?
P.S.: "Nema takve datoteke ili direktorija" literally translates to "So such file or directory".

Try this

```

#include<stdio.h>

int main(void)
{
    printf"Hello World\n";

    return 0;
}

```

Then compile the code
```

gcc -o hello hello.c

```

Execute the code
```

./hello

```

Should work.  You can also use g++ as it will compile C or C++ code.

---

### Post by Trail on 2008-02-14
```

#include<stdio.h>

int main(void)
{
    printf"Hello World\n";

    return 0;
}

```

That's C, not C++, it contains a syntax error, and for C++ you shouldn't include "stdio.h" :)

@OP: cc1plus is an internal gcc program that handles the c++ code if i remember correctly. So it appears some part of gcc is broken. Try reinstalling it (maybe --purge too). Also make sure you have the package "build-essential" installed.

---

### Post by marufaberlin on 2008-02-14
I wouldn't think that's c++ code, it uses printf!
But I agree, it's not c code either. Maybe it should be called c-- :-D

---

### Post by natirips on 2008-02-14
First of all, my problem has been solved.

Second, this code
```
#include<stdio.h>

int main(void)
{
    printf"Hello World\n";

    return 0;
}
```
is a lol...
1) In c++ it is cstdio, not stdio.h (which goes for c)
2) printf syntax follows general syntax used for all other fnctions: 
```

functionname(arg1,arg2,/*...,*/argn);

```
Where the guy above forgot brackets.

Third, I do know basics of c and c++:lolflag:.


P.S.: I just hope I don't get banned from this forum for such a harsh post (like I got banned from some other forums lately :()

---

### Post by LaRoza on 2008-02-14
> **natirips said:**
> 

P.S.: I just hope I don't get banned from this forum for such a harsh post (like I got banned from some other forums lately :()

It wasn't harsh, just true.

For the rules of this forum see the Codes of Conduct link in my sig.

For programming, see the Programming Talk forum, it is under "Development and Programming" on the main page.

---

