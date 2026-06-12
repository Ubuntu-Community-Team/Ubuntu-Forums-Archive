---
title: "Qt4 + netbeans6.1 + Ubuntu"
date: 2008-05-18
forum: General Help
---

### Post by Bucephalus01 on 2008-05-18
If anyone has got this combination working. I would greatly appreciate some help.

I have completed most the steps in a tutorial on qtforum which is for cygwin, netbeans 6.01 and qt. I have removed the red underlining of the include statements. I just can't get the project to run from netbeans.
After I go into the netbeansproject folder and enter the project folder for the specific project, I execute the following.

qmake -project CONFIG+=console
qmake

Then I go into netbeans and build the project and then run it.
But I get the following output.

/home/bucephalus/.netbeans/6.1/bin/dorun.sh: 103: ./dist/Debug/GNU-Linux-x86/qtest1: not found
[Press Enter to close window]

Can anybody help?
PS: THe project I'm attempting is the first turorial (the Hello World tutorial) in the qt documentation.

---

### Post by kkkkdddd on 2008-05-18
Maybe you should edit /home/bucephalus/.netbeans/6.1/bin/dorun.sh

Change line 103:  ./dist/Debug/GNU-Linux-x86/qtest1
to use absolute path: /home/...  (the path to qtest1)

Maybe qtest1 is in another directory

To search whole system for file qtest1
find / -name qtest1 2> /dev/null

---

### Post by Bucephalus01 on 2008-05-18
Hey

Thanks, you put me onto the right path.
I found that qtest1 was being compiled immediately into the project folder:

bucephalus@Magnus:~/NetBeansProjects/qtest1$ ls
build  Makefile  nbproject  qtest1  qtest1.cpp  qtest1.o  qtest1.pro

So what I had to do then, based on a tutorial I was reading earlier is to right click on the project in the project window in netbeans and select properties down the bottom of the menu.

I then had to change select "Linker". 
Then I changed the output directory from:
dist/Debug/GNU-Linux-x86/qtest1

to:
qtest1

These two paths are relative to ~/NetBeansProjects/qtest1

thanks for your help.
Bucephalus

---

