---
title: "Processes dying unexpectedly upon startup."
date: 2007-09-19
forum: General Help
---

### Post by checho4 on 2007-09-19
I am running Kubuntu Feisty [64-bit].  Yesterday, I started up my computer and, after logging into KDE, the first thing to pop up is a window that says "The process for the trash protocol died unexpectedly."  What does this mean?  How do I fix the problem?  Any help would be greatly appreciated!

---

### Post by prince_niceguy on 2007-09-19
run one of the process which died suddenly from terminal... seems like some dcop issue... not sure for sure though..

---

### Post by checho4 on 2007-09-20
What exactly do I run?  I know it's the trash protocol, but I don't know how to run that.

When this started, I also had a problem with Amarok.  In my process table, everytime I try to open Amarok, I see "amarok" and "amarokapp".  However, nothing happens.  I can only kill "amarok".  I have an "amarokapp" for every time I tried to open amarok.  I've tried "kill" "killall" "kill -9" "killall-9" and rebooting, but I can't get "amarokapp" to close.

How do I get rid of a zombie?


Ok, if it's any help, I just found what MAY BE The problem.  I have another ext3 partition with all of my music, that is accessed through both Windows XP and Kubuntu.  However, when I try to navigate to that partition, Konqueror freezes on me.

---

### Post by checho4 on 2007-09-22
Well, I got Amarok to open now.  I had to go in through Windows and delete the trash folders.  However, I still can't access my music partition through Linux.

---

