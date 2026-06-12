---
title: "HOWTO SCRIPT: Automated custom kernel install"
date: 2008-03-23
forum: General Help
---

### Post by Doctor Debian on 2008-03-23
Hello everyone, today I would like to present my latest shell script: Corecu, a simple custom kernel installer for the end user. It takes most of the complication out of compiling the latest kernel, saving you quite a bit of time. Currently it has two options: Custom compile latest kernel with old options, and custom compile latest kernel with custom configuration. For nVidia and ATI drivers, I recommend Envy. Visit my blog @ docdeb.wordpress.com for other scripts.

HOW TO RUN:
1. Enter this command in the script's directory:
```
sudo ./corecu
```
2. Enter your option, and that's all! Unless you selected custom configuration...

KNOWN ISSUES:
For both options, you may be asked whether to include various drivers. For safety, I recommend entering "y" for all of these.

-Doc Deb

There's a GTK option and a command line option.

---

### Post by K.Mandla on 2008-03-24
Moved to General Help.

---

### Post by Doctor Debian on 2008-03-24
GTK script added with bug fixes.

Doc Deb

---

