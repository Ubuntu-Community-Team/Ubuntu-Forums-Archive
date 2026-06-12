---
title: "C++ Compiler"
date: 2006-12-22
forum: General Help
---

### Post by Zeek00 on 2006-12-22
New to the world of C++. I've written my first program... the famous Hello World program. I can't seem to compile it however. I have Kdevelope C/C++ developer. Does that come natively with a compiler?

When I type this into the command prompt.

`gcc hello_world.c '

I get this

gcc hello_world.c
hello_world.c:1:20: error: iostream: No such file or directory
hello_world.c: In function ‘main’:
hello_world.c:6: error: expected expression before ‘:’ token
hello_world.c:8:2: warning: no newline at end of file


Now the program I got from a book. That I have been reading to teach myself C++ and they say when compiled the program works fine. But obviously.. not working. Any words on how to use gcc better or is there a compiler with some purty :p  graphical interface to it? Any help thanks in advance.

Zeek

---

### Post by taurus on 2006-12-22
Maybe it's

```
g++ hello_world.c
```

---

### Post by Adramelech on 2006-12-22
I think Kdevelop dont come with gcc and stuff, check on synaptic if you have gcc and libc-dev...
Keep in mind that the compiler identifies  .c files to be C files instead of c++

Read: [http://www.advancedlinuxprogramming.com/alp-folder]("http://www.advancedlinuxprogramming.com/alp-folder") first chapter

---

### Post by Zeek00 on 2006-12-23
its not ` g++ hello_world.c ' when I type g++ it doesn't recognize the command same when I try to  view the man pages on g++. I'm pretty sure its gcc. Is there some major difference in coding c++ on a Linux machine verses a M$ windows machine?

Do i need to replace <iostream> with somthing?

---

