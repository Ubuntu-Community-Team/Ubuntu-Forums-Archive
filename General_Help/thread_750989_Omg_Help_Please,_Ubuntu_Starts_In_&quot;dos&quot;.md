---
title: "Omg Help Please, Ubuntu Starts In &quot;dos&quot;"
date: 2008-04-10
forum: General Help
---

### Post by scraghty604 on 2008-04-10
OK  so i changed the video driver under Preference>Apperence i think

i thought i did the right thing guess not it was set up for "intle test or virtual or somethign unforutly cant remeber

i changed it to the intel945 chipset

it said log out to apply

i did and it stop on what looked like dos

PLEASE HELP GUYS

i guess im gonna have to change it back  via some code but i know dink all about this

---

### Post by ibutho on 2008-04-10
You can get back into X by doing the following
[LIST=1]
[*]Login to the terminal
[*]Run ```
sudo nano /etc/X11/xorg.conf
```
[*]Go to the video card section and change the driver to "vesa" or "fbdev"
[*]Restart the login manager by doing ```
sudo /etc/init.d/gdm restart
```
[/LIST]
Hopefully that will help you get back into X. You can then reconfigure your card correctly. Also think about backing up important files before tinkering with any settings. ;)

---

### Post by reacocard on 2008-04-10
> **ibutho said:**
> You can get back into X by doing the following
[LIST=1]
[*]Login to the terminal
[*]Run ```
sudo nano /etc/x11/xorg.conf
```
[*]Go to the video card section and change the driver to "vesa" or "fbdev"
[*]Restart the login manager by doing ```
sudo /etc/init.d/gdm restart
```
[/LIST]
Hopefully that will help you get back into X. You can then reconfigure your card correctly. Also think about backing up important files before tinkering with any settings. ;)

in the first command, that should be X11, not x11, but aside from that, yes this should work.

---

### Post by ibutho on 2008-04-10
Thanks for spotting that error (I seem to make that error quite a lot even though I've been using Linux for years :)). I've fixed the post above.

---

### Post by scraghty604 on 2008-04-10
ok im in the config thing and i think i have chnaged this right

was

Section :device"
Identifier  "intel copr mobil 945gm
Boardname  Intel945
Busid  Pci 0 2 0
Driver i810
screen 0
vendername  intel

i deleted i810 and typed in vesa  is that right now what i cant find were to type the next line

---

### Post by ibutho on 2008-04-10
Yes thats correct. Change i810 to vesa or fbdev, save the changes and exit from the editor.

---

### Post by scraghty604 on 2008-04-10
i see it say 

^X to exit how do i do that how do i save it haha damn i feel like an idiot gotta leanr some time i guess thanxs guys

---

### Post by ibutho on 2008-04-10
If using nano, to save the file do CTRL-O and then to exit CTRL-X.

---

### Post by angry_johnnie on 2008-04-10
Save with Ctrl + O.  (that's O as in OMG!) :-)
To exit, press Ctrl + X

Edit:  Ibutho beat me to it!

---

### Post by scraghty604 on 2008-04-10
i guess i did somethign wrong casue it saved and  i retsarted using that code and it said

strating gnome manager
stoping gnome manager

screen flashed a few times and now right back were i started im gonna try the other driver u guys said

---

### Post by scraghty604 on 2008-04-10
also it wasnten very discriptive of which part was the video drive i saw i810 was used twice i changed both of them

---

### Post by scraghty604 on 2008-04-10
no luck same thing i also did this in recovery mood  that sis correct also i hope

---

### Post by scraghty604 on 2008-04-10
First one was 

Indentifer "Intel Corporation Mobile 945GM/GMS,943/940GML Express$

2nd
Indentifer  "device1"

Both have these inn common

Boardername "Intel 945"
Busid "PCI:0:2:0
Vendername "Intel"

---

### Post by Tomatz on 2008-04-10
Do this (at the command prompt):

**sudo dpkg-reconfigure -phigh xserver-xorg**

It should configure xorg.conf with basic settings. Then we can work out the correct driver for your gpu from a nice gui ;)

---

### Post by scraghty604 on 2008-04-10
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf .10080410011129

thhen goes back to prompt

---

### Post by Tomatz on 2008-04-10
> **Tomatz said:**
> Do this (at the command prompt):

**sudo dpkg-reconfigure -phigh xserver-xorg**

It should configure xorg.conf with basic settings. Then we can work out the correct driver for your gpu from a nice gui ;)


You need to do that^

---

### Post by scraghty604 on 2008-04-10
OMG AHAHAHAHHAHAHA ok well i restarted it and it is in now ok, if you dont mind thanxs for your timmeee can u help me set this up properly now i am back into ubuntu

---

### Post by scraghty604 on 2008-04-10
i did do that but then it just went back to promot after saying what i had typed but i restart the computer and seems to have  normal, but is it  do u mind helping setttgin up the right driver

---

### Post by Tomatz on 2008-04-10
> **scraghty604 said:**
> i did do that but then it just went back to promot after saying what i had typed but i restart the computer and seems to have  normal, but is it  do u mind helping setttgin up the right driver


Yeah lol i should have told you to reboot after ;)

---

### Post by scraghty604 on 2008-04-10
haha im a noob *** obv  so i looked again and it says intel experimental modsetting driver...is that the right one for my computer

acer 5570z intel 945 chipset what ever that means

---

### Post by Tomatz on 2008-04-10
Do this in a terminal:

**sudo lspci**

Then post the output

---

### Post by scraghty604 on 2008-04-10
scraghty604@scraghty604-laptop:~$ sudo lspci
[sudo] password for scraghty604:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Tomatz on 2008-04-10
when you done the **sudo dpkg-reconfigure xserver-xorg** did you choose the **intel** driver/option?

---

### Post by scraghty604 on 2008-04-10
when i did that this came up

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf .10080410011129

and went back to prompt, i didnt have any options?

thats when i was like this is lame an reset the computer and it worked :P

---

### Post by Tomatz on 2008-04-10
Thats great.

You done everything right. Using the intel driver instead of the 810 packaged driver is the prefered method ;)

Type this in a terminal and post the output:

**glxgears**

---

### Post by scraghty604 on 2008-04-10
Lol i got a gears thing, i didnt know if it was gonna end  so quit it let me know if i was suppsed to keep goign

ALSO NOTE  there one spot there were the frame rate went down at that exact time i  was flipping windows eles were, Which bring me back to the hole point i was changing the dirver( when watchign videos (i e youtube, very choppy and actuly seem a lil low on the quailty side but sound is smooth and fine)

anyways heres the out put

scraghty604@scraghty604-laptop:~$ glxgears
4918 frames in 5.0 seconds = 983.462 FPS
5055 frames in 5.0 seconds = 1010.985 FPS
5015 frames in 5.0 seconds = 1002.948 FPS
5019 frames in 5.0 seconds = 1003.739 FPS
5088 frames in 5.0 seconds = 1017.594 FPS
4946 frames in 5.0 seconds = 989.141 FPS
5070 frames in 5.0 seconds = 1013.902 FPS
5117 frames in 5.0 seconds = 1023.317 FPS
4979 frames in 5.0 seconds = 995.699 FPS
5073 frames in 5.0 seconds = 1014.570 FPS
4935 frames in 5.0 seconds = 986.955 FPS
4983 frames in 5.0 seconds = 996.551 FPS
5140 frames in 5.0 seconds = 1027.840 FPS
4974 frames in 5.0 seconds = 994.646 FPS
5103 frames in 5.0 seconds = 1020.467 FPS
5062 frames in 5.0 seconds = 1012.311 FPS
4976 frames in 5.0 seconds = 995.010 FPS
5118 frames in 5.0 seconds = 1023.542 FPS
4233 frames in 5.0 seconds = 846.421 FPS
3999 frames in 5.0 seconds = 799.790 FPS<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
4666 frames in 5.0 seconds = 933.103 FPS
4977 frames in 5.0 seconds = 995.307 FPS
5109 frames in 5.0 seconds = 1021.691 FPS
5004 frames in 5.0 seconds = 1000.641 FPS
4999 frames in 5.0 seconds = 999.799 FPS
5097 frames in 5.0 seconds = 1019.308 FPS
4924 frames in 5.0 seconds = 984.629 FPS
4946 frames in 5.0 seconds = 989.117 FPS
5008 frames in 5.0 seconds = 1001.461 FPS
4895 frames in 5.0 seconds = 978.951 FPS
5093 frames in 5.0 seconds = 1018.579 FPS
4983 frames in 5.0 seconds = 996.499 FPS
4965 frames in 5.0 seconds = 992.914 FPS
scraghty604@scraghty604-laptop:~$

---

### Post by Tomatz on 2008-04-10
Sorry lol should have told you to stop it. Everything looks fine The frame rate is about what i would expect from that gpu.

Glad its sorted now ;)

---

