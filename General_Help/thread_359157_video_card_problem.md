---
title: "video card problem?"
date: 2007-02-11
forum: General Help
---

### Post by johnny9794 on 2007-02-11
I have a problem with booting up edgy 6.10 live cd and dvd on rom drive.

ok, i booted edgy up with live cd and also tried live dvd, my problem is that i get so far booting up to where the desktop is suppose to show to explorer the live-disc or to install ubuntu from the desktop, I get on my screen stating input not supported so I thought it was my monitor "Acer AL1714", so i disconnected the acer and hooked up my other monitor
"Phillips 107 T6 crt" and tried booting the disc once again. I get on my Phillips stating "12k/36HZ Frequency is out of range". In the background of my speakers i can hear Ubuntu booting up, with the logon sound, But!!! no image at all.

Is the problem within my graphics card?

SYS Info:

CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz 800 FSB Hyperthreading.
Mobo: Asus p5gl-mx.
Ram: 1 gig DDR-SDRAM Dual Channel.
Graphics Card: Nvidia MSI NX6600 LE 256 mb

---

### Post by Stemp on 2007-02-11
> Is the problem within my graphics card?

I think it's a monitor detection error.
First you have to find informations about your monitor.
Then log into safety mode, and find the monitor part of the file /etc/X11/xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

you will find something like this :

```
Section "Monitor"
        Identifier      "NEC CI LC700"
        Option          "DPMS"
EndSection
```

Change it to : 

```
Section "Monitor"
        Identifier      "NEC CI LC700"
        Option          "DPMS"
        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 150.0
EndSection
```
 
Depending on the Horizontal and Vertical refresh rates of your monitor

---

### Post by johnny9794 on 2007-02-11
> **Stemp said:**
> I think it's a monitor detection error.
First you have to find informations about your monitor.
Then log into safety mode, and find the monitor part of the file /etc/X11/xorg.conf

Safe graphics mode? Nope that did not work, I cannot edit anything when i cannot see anything. 

I do not know what else to say. Other than i cannot see.

Anyone else with this same problem?

---

### Post by Stemp on 2007-02-11
> Safe graphics mode? Nope that did not work, I cannot edit anything when i cannot see anything. 

Press Ctrl+Alt+F1 to get to a text mode.

---

### Post by johnny9794 on 2007-02-11
> **Stemp said:**
> Press Ctrl+Alt+F1 to get to a text mode.

Install in text mode is there.
Noting happens when I hit Ctrl+Alt+F1 when i am at the screen with:

Start or Install Ubuntu
Start Ubuntu in Safe Graphics Mode
Install in Text Mode
Install in OEM mode
Install a command line system
check cd for defects
memory test
boot from first hard drive




should i install in text mode?

---

### Post by Stemp on 2007-02-11
Install Ubuntu first or choose Start or Install Ubuntu. Then when you have your screen problem, hit ctrl+alt+F1 to access a text mode, after modifying your xorg.conf hit ctrl+alt+backspace to restart your X server (the graphical part of Linux).

---

### Post by johnny9794 on 2007-02-12
> **Stemp said:**
> Install Ubuntu first or choose Start or Install Ubuntu. Then when you have your screen problem, hit ctrl+alt+F1 to access a text mode, after modifying your xorg.conf hit ctrl+alt+backspace to restart your X server (the graphical part of Linux).

Ok let me thank you for your time and help.

ok i got it intalled from "Install in Text Mode" and then when i boot up ubuntu and hit in ctrl+alt+f1 I see some text then that stoopid input not supported messege pops up.


Now i was on linuxguestions.org last night and found this.

[http://www.linuxquestions.org/questions/showthread.php?t=519047](http://www.linuxquestions.org/questions/showthread.php?t=519047)

But I will do anything i don't care how long it takes to get this to work lol.

Reason why I have used ubuntu before is cuz i had it on my old 1.7 celeron 2 months ago and now i got a new pc :/.

---

### Post by johnny9794 on 2007-02-12
> **Stemp said:**
> I think it's a monitor detection error.
First you have to find informations about your monitor.
Then log into safety mode, and find the monitor part of the file /etc/X11/xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

you will find something like this :

```
Section "Monitor"
        Identifier      "NEC CI LC700"
        Option          "DPMS"
EndSection
```

Change it to : 

```
Section "Monitor"
        Identifier      "NEC CI LC700"
        Option          "DPMS"
        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 150.0
EndSection
```
 
Depending on the Horizontal and Vertical refresh rates of your monitor

Ok I am able to get in the xorg.conf fileto edit it, here is a link to my monitor specs but i do not see anything about HorizSync and VertRefresh, where can i get this info?

[http://www.pricegrabber.com/search_techspecs_full.php/masterid=7777049/](http://www.pricegrabber.com/search_techspecs_full.php/masterid=7777049/)

---

### Post by Stemp on 2007-02-12
It's a lcd so you don't need to add Horizontal and vertical refresh rate.
So it must be a video card problem :(

I think it will be better to install Ubuntu using an alternate cd (text mode), you can get it there : [http://mirrors.cat.pdx.edu/ubuntu-iso/edgy/ubuntu-6.10-alternate-i386.iso](http://mirrors.cat.pdx.edu/ubuntu-iso/edgy/ubuntu-6.10-alternate-i386.iso) by example.

Once installed it will be easier to modify you xorg configuration.

---

### Post by johnny9794 on 2007-02-12
well yea i guess its vid card uhwell, thanx for the halp though :).

---

