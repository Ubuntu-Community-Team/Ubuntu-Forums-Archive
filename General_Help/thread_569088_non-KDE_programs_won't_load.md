---
title: "non-KDE programs won't load"
date: 2007-10-06
forum: General Help
---

### Post by IAmAnEvilTaco on 2007-10-06
I've got a fairly strange problem. I'm using KDE, and it will only run KDE branded programs. It won't run just about any of the plain ubuntu programs, including firefox. I installed ubuntu first, then the kubuntu package. I tried the patch offered here:

[http://ubuntuforums.org/showthread.php?t=364442](http://ubuntuforums.org/showthread.php?t=364442)

But it accomplished little, save giving me a warm fuzzy feeling when I didn't destroy my sudo. Running from the command prompt doesn't do anything, either.

---

### Post by kellemes on 2007-10-06
Running from terminal gives you no output at all?

---

### Post by IAmAnEvilTaco on 2007-10-06
Nope, it pretends to start to run, then just stops. When I try to run it via the gui I at least get the loading program message, but when I do so via terminal or command it does absolutely nothing. It does, however, work in plain ubuntu.

---

### Post by IAmAnEvilTaco on 2007-10-08
I can't run gedit from konsole, either. I get some input error 107 message and it locks and dies. it seems like the same problem the other programs are having.

---

### Post by IAmAnEvilTaco on 2007-10-10
I reinstalled from the cd, but used the kubuntu cd rather than applying kde afterward via patch. fixed it, it seems.

---

### Post by MDominic on 2007-10-13
I think I am having a similar problem.  It seems to happen randomly that I will click an icon to start a program or use my hotkey combination for same, and I will get the flashing icon indicating that it is starting, but then...nothing.  No program, no error, just nothing.  
When this happens, the only way to restore a normal state is restart X or restart the computer.  
I have observed this behaviour with a number of programs, including Firefox, K3B, Amarok, and others.  It does not happen in Gnome.  
I've posted about this over at the kde forums, but have not yet gotten a response. I would really like to continue using KDE but this is an unacceptable problem.  Any suggestions?

---

### Post by IAmAnEvilTaco on 2007-10-23
installing directly from the cd helps to an extent, but it seems that kde has different architecture than ubuntu and some of the other distributions, so the only way I'm seeing to make anything work is if you only use the stuff that comes bundled with kde. I gave up because of it. I'm sure there are libraries around that will give you the extended gnome functionality, debian, etc... that firefox and the rest need, but I never found them.

---

