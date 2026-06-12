---
title: "Install problems"
date: 2007-02-21
forum: General Help
---

### Post by hove99 on 2007-02-21
I have just bought a new computer:

ASUS P5B-E Mainboard
Geforce 8800 GTS
Intel Core2 Duo CPU
SATA and SATA2 Harddisk

I have tried both edgy and feisty CD's, but each time I get errors.

Using edgy live CD (32 bit), I get x-server error (failed to start due to no screens found).

Using edgy 64 bit live I get a grey ubuntu splash boot screen and an error after a while:

"BusyBox V1.1.3 (Debian1.1.3-2ubuntu30 Built-in Shell (ash)"

/bin/sh: can't access tty; job control turned off

Using feisty 64 bit (both live and alternate), the systems hangs with black screen.

Any advice? Have tried browsing the forum, and I found some similar cases, but nothing quite the same, because I can't install ubuntu at all.

---

### Post by taurus on 2007-02-21
Should try the alternate CD to install Edgy on your new machine.

---

### Post by Rofo on 2007-02-21
Hi, I just posted a similar message a few minutes ago. Like you I have an ASUS P5 board with SATA drives. Interestingly enough, when I disconnect the HDD (unplugging the SATA cable), the loading of Ubuntu 6.10 Live CD works fine.

-- Robert

---

### Post by Rofo on 2007-02-21
Hi, just solved the problem on my machine by moving the HDD SATA cable to another (Master) connector on the motherboard. Maybe you could try it as well?

-- Robert

---

### Post by hove99 on 2007-02-22
Are you using the 64-bit CD? Which graphic card are you using? I still get the error with x-server with the 6.10-cd's and the busybox error with the 32-bit 7.04 cd. The 64-bit 7.04 cd gives me a black screen after trying to launch the live CD.

Have anyone made the Geforce 8800 GTS (or GTX) work with Ubuntu?

---

### Post by revoltism on 2007-02-22
You could try editing you're xorg.conf or a dpkg if you get to the console. 

```
sudo dpkg-reconfigure xserver-xorg
```


```
sudo nano /etc/X11/xorg.conf
```

If "nvidia" won't work you could try the "vesa" driver (but then you won't have 3d support) and install the newest linux driver from nvidias homepage.


After you have saved just write "startx" from console.

---

### Post by kiaran on 2007-02-22
I too have a new Core 2 Duo system with a 8800 GTS. I am getting the "no screen found" error as well. Its really annoying because I'm sure if I could just install the damn thing I could install the video card drivers manually, if indeed wrong drivers are the problem.

I would really appreciate some help. I am downloading Feisty at the moment, so hopefully that works better...

---

### Post by hove99 on 2007-02-22
Using the thread:

[http://ubuntuforums.org/showthread.php?t=351205](http://ubuntuforums.org/showthread.php?t=351205)

, I managed to solve my problem by installing using the alternate CD and booting in to recovery mode (command line). Then I downloaded the latest linux driver from nvidia.com and transferred it to my 8800GTS computer to a folder using a memory stick.

Then I installed the package 'libc6-dev' from the alternate CD

sudo apt-get install libc6-dev

Then I ran:

sudo chmod +x "the name of the nvidia driver"

and from the folder, in which the driver is:

./"the name of the driver"

, and ignored warnings from the installer making the installer recomile som kernel or something :-) Then I could boot into Ubuntu (64-bit Edgy)

---

### Post by OldSeaDog on 2007-02-26
I also have the problem with feisty and ASUS motherboards, SATA drives and NVidia cards.  I have an ASUS M2N SLIDeluxe with a 4200 64X2 processor (AMD) with 2GB memory, a 320 GB SATA drive and a 250 GB EIDE drive.  I also have a NVidia GeForce 7300 video card from Fozconn.  The speicific error is:
"udevd-event [2031] :  run program '/sbin/modprobe' abnormal exit

BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu2) Built-in Shell (ash)
enter 'help' for a list of built-in commands

/bin/sh : can't access tty : job control turned off (initramfs)"

On one occasion it continued after a while writing events to the screen in a great gush I couldn't capture.  Subsequently I could type help once, then it was completely locked up where even the three-fingered salute wouldn't work.  Maybe I had better wait a while.

---

### Post by OldSeaDog on 2007-02-27
I didn't mention whaat version I was working with.  I have Herd 4 of feisty and the original problem arose wwith the 32 bit version, notwithstanding my hardware, since Edgy choked on th 64 bit version of edgy.  I have since tested it on the 64 bit version, same problem.  The 32bit version runs fine (as a LiveCD) on my 32 bit Acer 3003 laptop - 32 bit AMD.

OldSeaDog, the Geekosaur

---

### Post by goofeyfoot on 2007-03-05
Seadog:

I have the same problem.

I have similar equipment too.

Any advice, should you find any would be appreciated.

Thanks.

Michael

---

