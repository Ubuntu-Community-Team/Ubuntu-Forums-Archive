---
title: "How to convert  DOS command to Linux shell script"
date: 2008-02-13
forum: General Help
---

### Post by yinglcs2 on 2008-02-13
Hi,

I am trying to run a tutorial, It has a DOS command:

@java -cp "%~dp0\src;%~dp0\bin;C:/Program Files/Google Web Toolkit/gwt-user.jar;C:/Program Files/Google Web Toolkit/gwt-dev-windows.jar;./lib/gwtext.jar" com.google.gwt.dev.GWTShell -out "%~dp0\www" %* com.mycompany.mypackage.HelloWorld/HelloWorld.html


Can you please tell me how can i convert it to a linux shell script.
I know I need to change the path name. But what about stuff like 
%~dp0\src;%~dp0\bin

and 

"%~dp0\www" %*

What does that mean?

---

### Post by MobiusNZ on 2008-02-13
%~dp0 appears to be some kind of shortcut folder (like ~/ means /home/username). I'd suggest you look around for a src and www folder round your folder and just use standard filenames. Alternatively, look at using something like Ant to compile your project, that way it will work across platforms.

---

