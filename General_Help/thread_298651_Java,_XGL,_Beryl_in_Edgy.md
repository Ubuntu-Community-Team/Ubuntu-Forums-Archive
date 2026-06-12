---
title: "Java, XGL, Beryl in Edgy"
date: 2006-11-13
forum: General Help
---

### Post by destruego on 2006-11-13
Okay, so I Googled around a bit looking for a solution to the whole blank-screen in Java program problem when using Beryl and XGL (although I'm using a standard GNOME session instead of an XGL one since it bugs out whenever I use my volume hotkeys or disconnect my laptop from power). I saw someone recommend adding AWT_TOOLKIT="MToolkit" into /etc/environment and while that did work for me (as in Java windows weren't blank anymore) whenever I had a Java program open I would select a different window and two seconds later the focus would return to the Java window, and I wasn't able to interact with any other windows until I closed it. I was wondering if there are any workarounds or something (I'm using the latest Sun Java that Automatix installed, how I love Automatix) 'cause it's nice to be able to see the programs but I'm not too keen on not being able to do anything else while I have a Java prog running, and I don't want to switch to another Java client 'cause I'm still leery about tinkering with too many things.

I apologize if there is a post I missed on a fix for this (that isn't the AWT_TOOLKIT thingy), and I'd uber-appreciate if someone could direct me to said fix, or post one here or something.

Thanks!

---

### Post by andyrobo60 on 2006-11-13
I don't know if there is an easy fix but I think the problem is caused by java's swing GUIs not working in XGL. when I used compiz (I Stoped for this very reason). The fix I used was to run an XGL and standard desktop at the same time. you can do this by adding "1=Standard" in the "[servers]" tag of gdm.conf. this way you can Ctrl-Alt-F* between the two desktops (F7 was XGL desktop and F9 was standard desktop for me.)

---

### Post by destruego on 2006-11-13
Okay, thanks, I'll give it a shot. I know that Java progs run peachy keen when I'm using Metacity, it's just a bugger to switch between the two, since I always end up with some artefacts and choppiness. Hopefully this works. Thanks again! :D

---

### Post by destruego on 2006-11-13
Oh yeah I completely forgot to ask this in either post... Is there any way to set Beryl or Metacity to only affect certain windows? In this case, tell it that any Java window is to be decorated by Metacity instead of Beryl, that way there won't be any problems. I've been looking for something like that but haven't found anything as of yet... Any ideas, anyone?

---

### Post by blindd0t on 2006-12-23
It took quite a big of digging around via Google, but I finally found some answers.  The AWT_TOOLKIT fix doesn't seem to do the job very well, especially with Netbeans.

First, in JDK1.6 U1B01 the problem has been fixed for Compiz (not Beryl, however).  You can download the new JDK6 U1 build from **[here]("http://download.java.net/jdk6/binaries/")**.  If you wish to switch from Beryl to Compiz, follow (the *very* simple) instructions **[here]("http://www.ubuntuforums.org/showthread.php?t=308606&page=2&highlight=compiz+java#19")**.

Furthermore, if switching from Beryl to Compiz is not an option for you, you can alternatively launch your Java programs in a different Window Manager using xnest, which is explained further **[here]("http://www.ubuntuforums.org/showthread.php?t=136953&page=3&highlight=compiz+java+xnest#26")**.  Admittedly, many have stated that switching from Sun's JVM to IBM's fixed the problem for them, but not so for me.  You could always try that before you resort to using a different window manager with xnest.

I hope this helps!

-d0t-

---

