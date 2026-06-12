---
title: "[SOLVED] Problems with gcc compiler"
date: 2008-06-23
forum: General Help
---

### Post by carson11 on 2008-06-23
For some reason, I can't run the executable generated from compiling a c and c++ program with the gcc compiler.  The c program gives an error: "bash: com: command not found" when I try to run the executable file by typing the name of the file, com, into the terminal in the directory it's in.  The c++ program doesn't display any errors and doesn't do anything at all.  
To compile, I'm using the command:  "g++ test.cxx -o test" for the c++ program and "g++ com.c -o com" for the c program.
I have the gcc compiler on my windows machine and it generates an executable which works perfectly.

Thanks for any help.

---

### Post by sdennie on 2008-06-23
You need to type:

```

./test

```

Or

```

./com

```

By default the current directory is not in the path so you have to explicitly specify what you are referring to.

---

### Post by |{urse on 2008-06-23
sudo apt-get install gcc, try compiling it with gcc instead of g++. same problem?

---

### Post by |{urse on 2008-06-23
lol so thats why i always end up with a.out lmao :lolflag:

---

