---
title: "no sound?"
date: 2008-05-04
forum: General Help
---

### Post by jojotjuh on 2008-05-04
Hi all!
First of all:
I'm new to ubuntu. I'm quite experienced with windows but ubuntu is really different.
now to the problem:
I'm using Hardy (8.04) desktop i386 version (non alternate)

in terminal:
```
joey@joey-ubuntu:~$ sudo lspci | grep Audio
[sudo] password for joey: 
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
joey@joey-ubuntu:~$ 

```


```
joey@joey-ubuntu:~$ sudo lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS649 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
03:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
03:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)

```

I hope this is enough information for you to help me.

---

### Post by mali2297 on 2008-05-04
Have you checked that the sound channels are unmuted?

Use gnome's volume control or run
```

alsamixer

``` 
in the terminal.

---

### Post by jojotjuh on 2008-05-04
Thank you for your answer, but my sounds are all on 100% and none is muted and it still wont work
but thanks for answering anyway :)

---

### Post by mali2297 on 2008-05-04
Try the solution given in this [thread]("http://ubuntuforums.org/showthread.php?t=667586").

EDIT: Nevermind, you've already seen that.

---

### Post by jojotjuh on 2008-05-04
> **mali2297 said:**
> Try the solution given in this [thread]("http://ubuntuforums.org/showthread.php?t=667586").

EDIT: Nevermind, you've already seen that.

yep. saw it, didn't work.. =/

thanks anyway :D

EDIT: by the way, in windows, i have realtek for audio program but here it states azalia. is that the problem?

---

