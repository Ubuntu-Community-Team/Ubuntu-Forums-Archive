---
title: "gcc -fno-rtti / building jogl"
date: 2005-07-05
forum: General Help
---

### Post by geearf on 2005-07-05
Hello,

i m trying to build a jogl amd64 version with ant and i am running into some problems.

Last time i did it was with a FC3 and all went fine.

But now i tried different jogl / java versions and still the same error, i guess the error is coming from gcc .

[cc] cc1: warning : "-fno-rtti" is valid for C++ but not for C/ObjC

Thanks for any help on this :)

gcc --version
gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)

edit : 
I've tried everything i coul,d i think the problem may be deeper : 
[cc] cc1: attention : "-fno-rtti" is valid for C++ but not for C/ObjC
       [cc] cc1: attention : "-fno-rtti" is valid for C++ but not for C/ObjC
       [cc] cc1: attention : "-fno-rtti" is valid for C++ but not for C/ObjC

BUILD FAILED
/home/john/jogl/make/build.xml:1107: The following error occurred while executing this line:
/home/john/jogl/make/build.xml:857: The following error occurred while executing this line:
/home/john/jogl/make/build.xml:812: gcc failed with return code 1

line 1107 is :         <antcall target="c.compile.jogl.linux.amd64" />
line 857 is :       <antcall target="c.build" inheritRefs="true">
line 812 is :  rtti="false">

---

### Post by geearf on 2005-07-05
up  \\:D/

---

### Post by geearf on 2005-07-06
:grin:

---

### Post by geearf on 2005-07-06
with exactly the same setup on an ubuntu 32 bit i have no problem.

Please help :)

---

### Post by geearf on 2005-07-07
:cry:

---

### Post by geearf on 2005-07-08
snif

---

### Post by geearf on 2005-07-08
I've tried everything i could the problem may be deeper : 
[cc] cc1: attention : "-fno-rtti" is valid for C++ but not for C/ObjC
       [cc] cc1: attention : "-fno-rtti" is valid for C++ but not for C/ObjC
       [cc] cc1: attention : "-fno-rtti" is valid for C++ but not for C/ObjC

BUILD FAILED
/home/john/jogl/make/build.xml:1107: The following error occurred while executing this line:
/home/john/jogl/make/build.xml:857: The following error occurred while executing this line:
/home/john/jogl/make/build.xml:812: gcc failed with return code 1

line 1107 is :         <antcall target="c.compile.jogl.linux.amd64" />
line 857 is :       <antcall target="c.build" inheritRefs="true">
line 812 is :  rtti="false">

---

