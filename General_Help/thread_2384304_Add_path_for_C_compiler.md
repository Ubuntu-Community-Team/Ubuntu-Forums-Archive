---
title: "Add path for C compiler"
date: 2018-02-05
forum: General Help
---

### Post by ranjan549 on 2018-02-05
Hello All,

[COLOR=#111111][FONT=Ubuntu]My program file is using header files in /usr/include/linux and some other header files (such as slabs.h) in /usr/src/linux-headers-4.13.0-26/include/linux The gcc compiler fails to recognize the header files from the later and throws fatal compilation error How to add the later path for compilation.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried giving absolute path for the header files.
I also tried command like gcc -I {additional path} myFile.c -o myFile[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Please tell me how to add the path. Any help will be appreciated. Thanks in advance[/FONT][/COLOR]

---

### Post by steeldriver on 2018-02-05
Hello and welcome to the forums

What you have done sounds correct - please show us the complete command and actual error message from the compiler

---

