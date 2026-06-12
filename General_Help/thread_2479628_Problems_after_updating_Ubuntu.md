---
title: "Problems after updating Ubuntu"
date: 2022-09-30
forum: General Help
---

### Post by rafael-caro on 2022-09-30
Just updated to 22.04, but when I entered in my home directory I found a huge amount of folders and files that look like program files, but they're in my home directory. I don't know where were those files before, but now it's difficult for me to find some directories quickly.
Other problem I had is that I lost my gpp compiler and ALL standard libraries (such as iostream, fstream, string or cmath) for C++, I tried to install again gpp but I didn't recover those libraries.
Should I move the files that appeared in my home directory? Should I delete them? How can I recover my C++ libraries?

---

### Post by Impavidus on 2022-10-01
Release upgrades don't normally affect your home directory, so are you really sure you're looking at your home directory?

gpp is the general purpose preprocessor. The C++ compiler is g++. The standard libraries are a vital part of the OS, but the header files may be missing – although a release upgrade shouldn't remove them. All assuming you installed all of that through the package manager from the official repositories.

---

