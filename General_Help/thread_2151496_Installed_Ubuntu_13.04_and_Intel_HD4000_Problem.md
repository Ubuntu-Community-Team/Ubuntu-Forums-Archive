---
title: "Installed Ubuntu 13.04 and Intel HD4000 Problem"
date: 2013-06-04
forum: General Help
---

### Post by kirtan on 2013-06-04
I just Installed Ubuntu 13.04 x64 but when it starts mouse cursor move very slowly when i Try to operate it and also Not able to change resolution more than 1024x768. my machine is i7 3770K and Graphics is On Board Intel HD 4000. Seems it have not detected my graphic card. what would be the problem ? please help me I am trying to use Ubuntu from last 2 release but same problem occurred before too but though will be fixed in 13.04 but in 13.04 also the same thing is happening.

My Processor Model and Graphics Card on Windows Machine Device Manager.

[IMG]http://s21.postimg.org/t08i6k2k7/6_5_2013_1_30_26_AM.jpg[/IMG]

---

### Post by ajgreeny on 2013-06-04
I am very surprised that you can not get the Intel HD4000 integrated graphics working in these recent versions of Ubuntu.  I have Xubuntu 12.04.2 running faultlessly with an Intel i5-3570K cpu also with the HD4000 graphic card and saw no problems of any sort on installation, nor after many updates of the system, and the addition of the updated xserver-xorg-video-intel package from a ppa to give me full SNA acceleration.  Is the intel graphics the only one available or do you have hybrid intel/nvidia graphics which could need [**bumblebee**]("https://wiki.ubuntu.com/Bumblebee") added.

---

### Post by kirtan on 2013-06-05
I have no other graphic card just HD 4000 which is on Board.

---

### Post by ajgreeny on 2013-06-05
Sorry, in that case I am baffled.  I thought the drivers for the intel integrated HD4000 chip worked in all Ubuntu OSs since at least 12.04, so assumed that your system should be fine.

---

### Post by thotz on 2013-06-06
Maybe you find here some information: [http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

---

### Post by kirtan on 2013-06-12
tried those commands in link it shows some Xeon thing instead of HD 4000 as Graphic card

---

### Post by thotz on 2013-06-13
Another way would be to report a bug if nobody can help here ([https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)).

---

### Post by neuropa on 2013-06-28
I'm having the same problem!
I tried with Ubuntu 13.04, Ubuntu Gnome 13.04, Linux Mint 15 and Fedora 18.

My system board is Intel DZ77BH-55K, CPU Intel Core i7 3770-K.
```
lspci | grep -i vga 
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09).
```

In System Information I can see Graphics: Intel Ivybridge Desktop
Max screen resolution that I can set is 1024x768!

Any help?
Thanks!

---

### Post by Sergius14 on 2013-06-28
I have the same onboard card and I have a much more better experience with Intel drivers:

[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

Give it a try.

---

### Post by neuropa on 2013-06-29
> **Sergius14 said:**
> I have the same onboard card and I have a much more better experience with Intel drivers:

[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

Give it a try.

Thank you Sergius14. I installed Intel Linux Graphics Installer version 1.0.1 for Ubuntu 13.04 (64-bit), but nothing has changed.
Mouse cursor sill moves very slowly and screen resolution is 1024x768.
How can I check which driver is using Ubuntu? And how can I change it?

---

### Post by Sergius14 on 2013-06-29
Excuse me to insist something litte obvious, but just to double check: After you install Intel Linux Graphics, did you install the drivers?

You have to open this App and then let it install the right drivers for you.

Have completed with greens OK on all steps?


If still not working, try to boot from a Live CD/DVD/USB to check if your system somehow corrupted or not.


You processor / video card is definetelly suported.

---

### Post by neuropa on 2013-07-01
Yes, of course... I did it! :-)
This problem is present in every live OS that I have tested: Ubuntu 12.04 LTS, Ubuntu 13.04, Linux Mint 15 and Fedora 18.

Now I have installed Fedora 18 on HD and, after system upgrade via "yum update" the problem is gone away!
I would like to return using Ubuntu and so I wonder what upgrade (maybe kernel?) fixed this.

I can't still change screen resolution, that is locked to 1024x768 even if my graphic card and monitor support 1920x1080!

Any help is still appreciated...

---

