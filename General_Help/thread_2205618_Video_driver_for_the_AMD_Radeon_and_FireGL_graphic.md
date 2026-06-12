---
title: "Video driver for the AMD Radeon and FireGL graphics accelerators."
date: 2014-02-14
forum: General Help
---

### Post by tvanworth on 2014-02-14
Hello i am very new Ubuntu and Linux i have recently decided to use Ubuntu 12.04 instead of windows 8. I want to install the proprietary driver/drivers for my graphics card but when i go to check there are three that say the same thing, I am not for sure what to do from here i don't want to break anything.



:D Thank you and have a nice one.

---

### Post by deadflowr on 2014-02-14
Firstly, what's your card?
This can help us figure if one driver is better then another.
Secondly, what are the name(s) of the drivers they list?

---

### Post by QIII on 2014-02-14
Also, which "dot release" of 12.04 you are using may be important.

---

### Post by tvanworth on 2014-02-14
[COLOR=#4D4D4D][FONT=helvetica]AMD Radeon HD 7660G. when i open the additional drivers application that the system comes with it says "Video driver for the AMD radeon and FireGL graphics accelerator" how would i go about finding the actual name of these drivers its showing me?[/FONT][/COLOR]

---

### Post by tvanworth on 2014-02-14
12.04.4

---

### Post by tvanworth on 2014-02-15
ill be sure to put these specs in the tags next time i didn't think of doing so sorry about that

---

### Post by tvanworth on 2014-02-15
So after a few hours tonight my laptop started over heating more so than usual, i decided to look up a few things and found i need a catalyst graphics driver and that AMD supports a driver for Linux. 
[http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx)
On this web page it says this driver is supported on Ubuntu 12.04.2 and 13.10. Now i have a some questions and i hope i am not asking to many at once, should i switch to one of these releases(if so which one is best), i've also read there is an open source driver that i can use but as well as playing games already supported on Linux i want to try getting some windows games working with wine such as Starcraft 2 and quake does this open source driver work like the AMD supported driver?

---

### Post by Mark Phelps on 2014-02-15
The open source driver doesn't have the hardware acceleration needed for gaming and it doesn't do anything to handle processor speed to affect heating.

You should use the AMD restricted drivers, instead.

---

### Post by tvanworth on 2014-02-15
Ok do you suggest i switch versions of Ubuntu to one of the supported ones or is there a way i can download the driver via terminal and have it working correctly on the version im using 12.04.4?

---

### Post by tvanworth on 2014-02-15
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

i just tried this and it seems to have worked

---

