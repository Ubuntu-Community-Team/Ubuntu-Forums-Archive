---
title: "compiling problems"
date: 2008-03-15
forum: General Help
---

### Post by Sveet on 2008-03-15
when trying to use programs that are not found in the add/remove database, the most common thing to get is the source in a tar file. when using this to compile i get an error saying my C compiler cannot make executables.

---

### Post by confused57 on 2008-03-16
> **Sveet said:**
> when trying to use programs that are not found in the add/remove database, the most common thing to get is the source in a tar file. when using this to compile i get an error saying my C compiler cannot make executables.
Maybe this will help:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Do you have build-essential installed?

---

### Post by Sveet on 2008-03-16
i installed it but i get a new error, ERROR1

---

### Post by geraldm on 2008-03-16
Please provide details on what command you tried, and exactly what that command returned.

---

### Post by Sveet on 2008-03-16
./configure
everything fine

make
a couple internal file errors, which id assume is the programmers fault, but then i get an error on the object file (Error 1) then it says leaving directory and i get a Dir error: Error2

---

### Post by mc4man on 2008-03-16
You should post what app your trying to compile and from the terminal the last 12 lines or so from the make attempt

---

### Post by pdboy on 2008-03-18
i think error 1 means that you do not have privileges to access some folder. try installing it as root.
;)

---

