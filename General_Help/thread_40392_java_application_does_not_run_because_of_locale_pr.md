---
title: "java application does not run because of locale problem"
date: 2005-06-08
forum: General Help
---

### Post by ahmetaa on 2005-06-08
Hello

i am trying to install IntelliJ IDEA, a popular java IDE under ubuntu 5.04. Installer for the IDE is also written in java, when i try to run the installation, it throws an exception as:

"current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultInvocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)... "

Obviously it is related with Ubuntu's locale configuration. i am not really good in linux. i checked some similar issues in the forum without a real solution. Can anyone help me out? i am planning to move all my development to Linux. 

i installed AMD 64 bit  JDK and JRE 1.5.0_03 already. My ubuntu is also AMD64.

---

### Post by defkewl on 2005-06-09
Try installing the locales using synaptic

---

### Post by ahmetaa on 2005-06-09
well, how will i do that? i haven seen no locale installation in synaptic i tried several -reconfigure locales stuff but no luck. there is no useful information i could use in the forums.
sadly, back to windows until i find a real fix.

---

### Post by jmpelletier on 2005-08-10
Hi,

I have the same problem. I tried installing sun j2sdk 1.4.2_04 and 1.4.2_08 and both have problem detecting the local settings of linux (5.04 amd64). The jdk1.5 dont have the same problemes but the Oracle Jdeveloper and Oracle AS i am tring to run both need 1.4.2_04 to run.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=12954](https://bugzilla.ubuntu.com/show_bug.cgi?id=12954)

This post seems to be pointing in the right direction but the solution dont work with me. I tried make a lymbolic link but with no result. 

Does anyone found a fix for this?

---

### Post by tigertiger on 2005-08-17
Hi everybody,

I don't have a fix for the unsupported locales problems, but I think I know where the problem lies: the X11 libraries need to dynamically load the locale support code from /usr/X11R6/lib/X11/locale/lib/common. In amd64, these are the 64-bit libraries. If you use any 32-bit program, it will not be able to load these.

There is actually a similar problem with pango libraries.

I haven't found out how to circumvent this problem yet, though.

-Christoph

---

### Post by tigertiger on 2005-08-17
I found one way to circumvent the problem: you can set the directory to load the X11 locale from using the variable XLOCALEDIR. The 32-bit libraries for this can be found in the package libx11-6.

* Copy the directory /usr/X11R6/lib/X11/locale/ to another directory, e.g. /usr/local/locale32.
* Get the 32-bit libraries from  the /usr/X11R6/lib32/X11/locale/lib/common or the package libx11-6 and copy them into /usr/local/locale32/lib/common.
* Set the environment variable XLOCALEDIR=/usr/local/locale32 before running a 32-bit program.

This circumvents the problem, but does not completely fix it (you have to set the variable manually for all 32-bit programs). The better way would be to fix the libraries in ia32-libs to use different default paths than the 64-bit version.

NOTE: I also found copies of the 32-bit libraries in /usr/X11R6/lib32/X11/locale/lib/common. However, this directoy tree does not contain the non-library files, so it is ignored by libX11. But you can use them to build the 32-bit alternate locale tree.

---

### Post by edsel on 2005-09-29
[QUOTE=tigertiger]Hi everybody,
I don't have a fix for the unsupported locales problems, but I think I know where the problem lies: the X11 libraries need to dynamically load the locale support code from /usr/X11R6/lib/X11/locale/lib/common. In amd64, these are the 64-bit libraries. If you use any 32-bit program, it will not be able to load these.
There is actually a similar problem with pango libraries.
I haven't found out how to circumvent this problem yet, though.
-Christoph[/QUOTE]
I have the same observation and a work around.  Basically the 32 bit jvm opens /usr/X11R6/lib32/libX11.so.6.2.  This is the correct library.  However within this library it references /usr/X11R6/lib/X11/locale.  Within this locale directory is a bunch of files which it opens and eventually it will want to open /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2.  Naturally this is the 64-bit library and things start failing from this point.  What we need to do is convince libX11.so.6.2 to use /usr/X11R6/lib32/X11/locale/lib/common/xlcUTF8Load.so.2.
I've managed to do this by editing /usr/X11R6/lib32/libX11.so.6.2 using emacs (a binary editor).
For the complete writeup on how to do this hack, I wrote it up in my blog at [http://www.adap.org/~edsel/blog/archives/42]("http://www.adap.org/~edsel/blog/archives/42")

---

### Post by tpoindex on 2006-01-11
[QUOTE=edsel]I have the same observation and a work around.  Basically the 32 bit jvm opens /usr/X11R6/lib32/libX11.so.6.2.  This is the correct library.  However within this library it references /usr/X11R6/lib/X11/locale.  Within this locale directory is a bunch of files which it opens and eventually it will want to open /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2.  Naturally this is the 64-bit library and things start failing from this point.  What we need to do is convince libX11.so.6.2 to use /usr/X11R6/lib32/X11/locale/lib/common/xlcUTF8Load.so.2.
I've managed to do this by editing /usr/X11R6/lib32/libX11.so.6.2 using emacs (a binary editor).
[/QUOTE]


I found an easier solution, it works in Breezy for AMD64:

export XLOCALELIBDIR=/usr/lib32/X11/locale

I have a small helper script to run 32bits applications, make sure you have
the 'linux32' package installed.  I have this script named $HOME/bin/32, and
of course $HOME/bin on my PATH:

#!/bin/bash
export XLOCALELIBDIR=/usr/lib32/X11/locale
PATH=$HOME/bin/32bit:$PATH exec linux32 $*


e.g., to run a 32 executable that needs this help, I run

    32 /usr/local/java14/bin/java ..... .....


I'm updating this post, as it shows up frequently in a google search on the topic.

---

### Post by mariuz on 2006-03-21
thanks had the [same errors]("http://mapopa.blogspot.com/2006/03/installing-oracle-on-ubuntu-breezy.html") with oracle *64bit* installer, now i copied the libXp* from my 32bit box and oracle  installer started :mrgreen:

---

### Post by eschwalb on 2007-01-16
I had a similar problem while trying to install Maple9.5 in Edgy AMD64.  This post got me most of the way there:  [http://ubuntuforums.org/showthread.php?t=274407](http://ubuntuforums.org/showthread.php?t=274407)
but I had to use topindex's export command to get the installer to work, and to run the application itself.  Thanks for the help

---

### Post by fmachado on 2007-02-15
Hi all,

I had the same problem with Edgy64 + Weblogic 8.1.6.

```

fmachado@pc03:/opt/bea816/weblogic81/workshop# ./Workshop.sh 
current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultCurrent locale is not supported
java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
        at sun.awt.motif.MWindowPeer.init(MWindowPeer.java:97)
        at sun.awt.motif.MFramePeer.<init>(MFramePeer.java:58)
        at sun.awt.motif.MToolkit.createFrame(MToolkit.java:209)
        at java.awt.Frame.addNotify(Frame.java:472)
        at java.awt.Window.addNotify(Window.java:413)
        at java.awt.Window.show(Window.java:459)
        at java.awt.Component.show(Component.java:1133)
        at java.awt.Component.setVisible(Component.java:1088)
        at workshop.core.util.SplashScreen.display(SplashScreen.java:26)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:324)
        at workshop.core.Workshop.start(Workshop.java:44)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:324)
        at workshop.core.Starter.invokeStart(Starter.java:38)
        at workshop.core.Workshop.main(Workshop.java:24)

```

I've fix this with

```
export XLOCALELIBDIR=/usr/lib32/X11/locale
```

Thank you all! :) 

Fernando Machado

---

