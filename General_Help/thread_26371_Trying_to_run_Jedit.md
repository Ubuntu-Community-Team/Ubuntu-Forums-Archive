---
title: "Trying to run Jedit"
date: 2005-04-12
forum: General Help
---

### Post by jmeadows111 on 2005-04-12
I am trying to run Jedit (a java-based text editor) in Ubuntu 5.04. I have installed the JRE (1.5), and installed both libgcj5-awt and libgcj4-awt, but still get the error at the  end of this posting when I try to run Jedit. I think the issue is with gnu.awt.gtk.GtkToolkit, but I don't know what else to install. Jedit worked fine under Fedora core 2 and WIndows XP. Any ideas?

Here is the error

[error] main: Exception in thread "main"
[error] main: java.awt.AWTError: Cannot load AWT toolkit: gnu.awt.gtk.GtkToolkit  not found in [file:/usr/share/jed
[error] main: it/jedit.jar, core:/]
[error] main:    at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.4.0 .0)
[error] main:    at ja
[error] main: va.awt.Component.getToolkit() (/usr/lib/libgcj.so.4.0.0)
[error] main:    at java.awt.Component.getFontMetrics(jav
[error] main: a.awt.Font) (/usr/lib/libgcj.so.4.0.0)
[error] main:    at org.gjt.sp.jedit.gui.SplashScreen.SplashScreen() (Unkno
[error] main: wn Source)
[error] main:    at org.gjt.sp.jedit.GUIUtilities.showSplashScreen() (Unknown So urce)
[error] main:    at org.gjt.sp.
[error] main: jedit.jEdit.main(java.lang.String[]) (Unknown Source)

---

### Post by slatkin on 2005-04-13
You need to install the JDK from Sun, or at least I did. I was having the same problems as you but now it's working great.

Download the JDK .bin file from Sun ([http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp), Update 2, Linux Self-extracting file).

Install java-package (apt didn't work for me for this even though i do have multiverse enabled, so I had to download it from [http://packages.ubuntu.com/hoary/misc/java-package](http://packages.ubuntu.com/hoary/misc/java-package) and dpkg -i it).

Type "fakeroot make-jpkg jdk-1_5_0_02-linux-i586.bin" and go through the options (filling in your name, accepting the license). This will make a .deb file you can easily install with dpkg.

After all that, jEdit worked perfectly for me.

Note that I HAD to use the Sun JDK. There is a free-java-jdk package in the repository which did not work as far as executing jEdit.

---

### Post by jmeadows111 on 2005-04-13
I already have the SUN jdk installed:

echo $JAVA_HOME = /usr/java/jdk1.5.0

but I will try it this way to see if it makes a difference. Thanks for responding!!

John

---

### Post by srr_steve on 2005-04-20
I had trouble getting jedit to run as well, infact was getting the same error until I installed JDK from Sun and did what slatkin said, now all is well

thanks

---

