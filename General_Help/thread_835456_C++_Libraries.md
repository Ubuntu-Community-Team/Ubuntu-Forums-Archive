---
title: "C++ Libraries"
date: 2008-06-20
forum: General Help
---

### Post by elmoosecapitan on 2008-06-20
Hi Everyone,

Where can I find a list of the C++ headers/libraries that have been installed on my distro?

More specifically, I am trying to find a header that will allow me to generate graphics, e.g., circle(x,y,r) and rectangle(x1,y1,x2,y2).


Thanks!



richard

---

### Post by mempman on 2008-06-20
If there is any C/C++ code that you want to compile using the C API, simple use the #include directive.  The actual location of the headers and source object files are typically in /lib or /usr/lib.  However, you need not bother with any of this as long as you install build-essential (from apt-get), this package will install various libraries and tools such as make and gcc.

---

### Post by elmoosecapitan on 2008-06-20
I should probably clarify: I am programming with C++ and I want to write a program that involves graphics. I am not looking for the library that my computer is depended on but rather the library that I can code with. : )


Thanks!

---

