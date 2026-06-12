---
title: "Hello World"
date: 2007-05-24
forum: General Help
---

### Post by timdoc1 on 2007-05-24
I noticed there is a sample "hello world" package.

I'd like to test it.  Where is it kept?  I tried to gcc it, but it was not found in my path.

---

### Post by stylishpants on 2007-05-24
The package is called "hello", so run this command to see a list of all files installed by the program:

dpkg -L hello

This will only work if the package is already installed.

---

