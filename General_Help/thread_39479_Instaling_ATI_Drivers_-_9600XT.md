---
title: "Instaling ATI Drivers - 9600XT"
date: 2005-06-05
forum: General Help
---

### Post by Alex[RM-UK] on 2005-06-05
Hi, 

I am sort of new to linux, and I have never installed ATI drivers befor on Linux, and I know they are hard to install. 

I have found a few guides, one of them in the wiki. I downloaded the drivers by doing this:

```
sudo apt-get install xorg-driver-fglr
``` 

I then restarted my computer, opened up Konsole and download the ATI control center:

```
sudo apt-get install fglrx-control
``` 

I then restarted my PC again. Once it had booted up, I clicked on the Kmenu icon, and I saw ATI Control icon there. So I clicked on it to open it up. It then gave me this error:

```
Driver does not provide the FireGL X11 extensions!
Panel components will operate only partily.
``` 

When I click O.K to the error, it then opens the window for the ATI control. Here there are only 2 tabs, Information and TV out. 

I was expecting more tabs as such to setup OpenGL but I am thinking that they are not there due to something with the error. 

Please can someone help me to install the ATI drivers on my computer.

Kubuntu 5.0.4
KDE 3.4
ATI Radeon 9600XT
Abit NF7
AMD XP3200

I am wanting to install Cedega and it says I need to set up OpenGL first before I try to install Windows applications. The guide I am following for Cedega is  [Here](http://digital-conquest.ath.cx/wiki/index.php/Cedega_4.2.1-1_howto#Configuring_Your_Computer_for_Cedega)

Thank you very much if you will help  :)

---

### Post by enquiry on 2005-06-05
Installing the driver is not very hard. Follow this instruction: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)
If you want better 3D performance, you may install ATI's proprietary driver instead (before following the instrucion, install gcc -- the GNU C compiler -- using apt-get): [http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)

---

