---
title: "apt-get install libqt3c102-mt (Couldn't find package?!)"
date: 2005-09-10
forum: General Help
---

### Post by Richard Rowlands on 2005-09-10
I'm trying to get Skype working on Ubuntu 5.04 Hoary Hedgehog.  Reading the HowTo I can see that I'm supposed to install libqt3c102-mt.  However, I get the following error message when I try to do this :-

rrowlands@ubuntu:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libqt3c102-mt

Where can I find the libqt3c102-mt package?

Regards, Richard.

---

### Post by Juergen on 2005-09-10
It's in my list in Synaptic.

Did you enable the universe and multiverse repositories?
Look here [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by rwabel on 2005-09-11
[QUOTE=Richard Rowlands]I'm trying to get Skype working on Ubuntu 5.04 Hoary Hedgehog.  Reading the HowTo I can see that I'm supposed to install libqt3c102-mt.  However, I get the following error message when I try to do this :-

rrowlands@ubuntu:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libqt3c102-mt

Where can I find the libqt3c102-mt package?

Regards, Richard.[/QUOTE]
 are you on breezy or hoary? breezy doesn't have it but libqt3-mt

---

### Post by Richard Rowlands on 2005-09-11
Hi, thanks for the advice.  After adding the repositories I was able to install the packages I needed and am pleased to say that Skype is now running on my machine!

Many thanks, Richard.

---

