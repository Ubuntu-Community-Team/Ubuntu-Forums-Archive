---
title: "Execute a text file?"
date: 2007-07-26
forum: General Help
---

### Post by Sparky222B on 2007-07-26
How do you execute a text file within terminal? I'm trying to install the ATI driver, which is a .run extention.

---

### Post by luckyd on 2007-07-26
> sudo chmod a+x "/wherever/you/have/the/ file.run/"
> sh "/wherever/you/have/the/file.run

:)

---

### Post by HermanAB on 2007-07-26
A typical shell script (the equivalent of a DOS batch file) is just a text file.  If the file was created right, then the first line will give the shell a clue as to what to do with it.  It typically starts with: "#! /bin/bash" meaning that the file should be executed by the Bourne Again Shell.

So, if the file is marked as executable, then just run it:
$ sudo ./filename

If it isn't marked executable, then make it so:
# sudo chmod 754 filename

'Hope that helps!

Herman

---

