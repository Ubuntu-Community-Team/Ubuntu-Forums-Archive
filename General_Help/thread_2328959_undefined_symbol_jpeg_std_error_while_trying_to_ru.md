---
title: "undefined symbol: jpeg_std_error while trying to run java project"
date: 2016-06-26
forum: General Help
---

### Post by big.nima01gmail.c on 2016-06-26
I have a completed java project. I'm going to run it on ubuntu 14.4 x86. Project requirements are : [INDENT]   Sun Java JDK 1.6,  MATLAB Compiler Runtime (MCR) is installed (version   7.11),  v4v4lj, code.google.com/p/v4l4j, in order to work with video source (webcam),  OpenCV lib

 [/INDENT]
I've installed Oracle Java JDK 1.6, V4L4J 0.8.0, MCR 7.17 and and  OpenCV lib. I already set "LD_LIBRARY_PATH" and "XAPPLRESDIR"  environment variables. I tried to run it like this as mentioned in  project ReadME file :
[INDENT]   Saving an image to DB: in the src directory, execute: java -classpath   .:[mcr_root]/v717/toolbox/javabuilder/jar/javabuilder.jar:/usr/share/java/v4l4j.jar:./buildFaceRep_fromFile.jar   -Djava.library.path=/usr/lib/jni -Dtest.width=1024 UI.SaveToDB

 [/INDENT]
I got this error :[INDENT] java: symbol lookup error: /usr/lib/jvm/java-6-oracle/jre/lib/i386/libv4l4j.so: undefined symbol: jpeg_std_error [/INDENT]
Can anyone help me on this, Please? 
Regards...

---

