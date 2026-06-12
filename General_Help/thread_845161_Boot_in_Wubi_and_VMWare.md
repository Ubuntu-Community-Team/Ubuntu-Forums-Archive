---
title: "Boot in Wubi and VMWare?"
date: 2008-06-30
forum: General Help
---

### Post by NICU on 2008-06-30
Hello,

I'm new to the Wubi approach.  I've used Ubuntu for years, but recently had to have XP on a PC at home :(  I installed Ubuntu through Wubi, and now I want to know if there is a way to run my new Wubi/Ubuntu installation through VMWare.  I would like to run Ubuntu and Windows at the same time on the same PC without having to reboot.  
Thanks in advance for anyone with any insight.

---

### Post by uidb4056 on 2008-06-30
> **NICU said:**
> Hello,

I'm new to the Wubi approach.  I've used Ubuntu for years, but recently had to have XP on a PC at home :(  I installed Ubuntu through Wubi, and now I want to know if there is a way to run my new Wubi/Ubuntu installation through VMWare.  I would like to run Ubuntu and Windows at the same time on the same PC without having to reboot.  
Thanks in advance for anyone with any insight.

As far as I know it's not possible, you have to install fresh Ubuntu into your VMWare. Other option you can have is install Virtualbox inside Ubuntu and then install on it XP. The best option should depend on what you want to use on each OS because virtualization will put some restrictions on applications that have to access specific hardware.

---

### Post by ago on 2008-06-30
It is probably possible but it would take some work
andlinux is probably the path of least resistance for what you want

---

### Post by nooby on 2008-07-02
I have done something similar. 

I have same ubuntu.iso and one is used in WUBI and the 
other in the Sun's Virtual Box vbox. 

So if I start up vbox I can use ubuntu and still change/switch over to 
windows without having to reboot. 

So that should work in wmware too. 

But andlinux maybe works even faster. I have Ulteo in colinux and 
andlinux is just another colinux way of doing it. 

But the Firefox settings are maybe not easy to find from windows to ubuntu to ubuntu. 

You have three versions of Firefox. So not easy to find a way to sync bookmarks. 

Maybe better to have on on the net as back up so all of then can 
download the latest? 

Same with three versions of email programs.

---

### Post by gaf.stephanos on 2008-10-02
I want the same thing, so if anyone could do it, please inform me

---

### Post by gaf.stephanos on 2008-10-02
Hey guys, is there anyway to boot my wubi partitions (or .disk files) WHILE working on windows using vmware or any other tool ?
Thanks in advance

---

### Post by ago on 2008-10-02
it is theoretically possible but not at this stage. anyway if you use vmware there is not much point in using wubi inside it.

---

### Post by Virtua-Touch on 2008-10-02
Well, I know you can launch your windows partition in VBox, but I don't know about Ubuntu. However, I did find this one link. [http://ubuntuforums.org/archive/index.php/t-515212.html](http://ubuntuforums.org/archive/index.php/t-515212.html)

---

### Post by Orlsend on 2008-10-02
I call for **Andlinux** its free and does what you want.

---

### Post by daevyd on 2008-10-02
> **Virtua-Touch said:**
> Well, I know you can launch your windows partition in VBox, but I don't know about Ubuntu. However, I did find this one link. [http://ubuntuforums.org/archive/index.php/t-515212.html](http://ubuntuforums.org/archive/index.php/t-515212.html)

As I understand this, I can boot my Windows XP partition with Virtualbox on Ubuntu?  How do I do this?  I tried to use my Recovery Discs but I get an error message telling me that they aren't compatible with this PC model.  Unfortunately I 'need' Windows to run certain programs like OverDrive Media Console and a couple others for homeschool curriculum. My dependence on Windows is thankfully limited and I've been able to get my wife to switch over to Ubuntu due to a virus taking the life out of my Windows partition but if I can run my Windows partition from Virtualbox we'll be set.  I can just restore that partition, then.  Any help on this will be greatly appreciated.

---

### Post by wgbeckmann on 2009-04-18
Hi, you can start your WUBI-Installation with QEMU.
(But it's slow!)

Here is the Commandline:
```
qemu -L . -m 512 -kernel-kqemu -kernel c:\\ubuntu\\disks\\boot\\vmlinuz-2.6.27-7-generic -append "root=/dev/sda" -initrd C:\\ubuntu\\disks\\boot\\initrd.img-2.6.27-7-generic -hda c:\\ubuntu\\disks\\root.disk -hdb c:\\ubuntu\\disks\\swap.disk -localtime -no-acpi
```

Correct the driveletter and the filenames

wb

---

### Post by ac90b671 on 2009-05-14
I'm not sure if everyone in this thread is on the same page. As I understand it the goal is to have windows native installed and use wubi to have ubuntu native on the same partition (wubi writes to C:\ubuntu\disks\). Then to be able to use a windows virtual program to run the root.disk (ubuntu) image within windows. Please correct if that's not the idea.

---

### Post by dranorter on 2009-08-16
Well, andlinux looks great but doesn't work in 64 bit! T_T

I am seriously thinking of just switching back to Linux. Vista is not treating me well. For the moment though I need M$ OneNote... and I like touch gestures.

---

