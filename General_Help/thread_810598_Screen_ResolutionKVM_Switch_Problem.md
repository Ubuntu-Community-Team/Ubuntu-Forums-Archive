---
title: "Screen Resolution/KVM Switch Problem"
date: 2008-05-28
forum: General Help
---

### Post by fdepinto on 2008-05-28
I just installed a KVM switch.  I'm switching between a Vista box and an Ubuntu box.  Unfortunately neither operating system will hold the screen resolution after a reboot.  I set the resolution to 1280 x 1024 (native for my LCD monitor) in both operating sytems.  They both revert to 640 x 480 after reboot.

Any idea on how I can force Ubuntu and/or Vista to "stick" to 1280 x 1024 after reboot?

Thanks in advance.

---

### Post by phr0ze on 2008-05-28
Hardy will not even let my pick a resolution over 800x600 if I use a KVM.

When you boot, have you tried to make sure that the KVM is set to the system as it boots? In fiesty the option would be to remove the lower resolutions in XORG.CONFG but since Hardy that is not in there anymore.

:confused::confused:

---

### Post by bodhi.zazen on 2008-05-28
Sounds like a hardware problem, ie the KVM switch is not giving the proper information to the OS.

I advise you go with a different KVM switch.

---

### Post by fdepinto on 2008-05-28
I tried this question in the beginner forum, but didn't get any real answer.  

I just installed a KVM switch. I'm switching between a Vista box and an Ubuntu box. Unfortunately, Ubuntu 8.04 didn't hold the screen resolution after a reboot. I set the resolution to 1280 x 1024 (native for my LCD monitor) before I installed the KVM switch, but after I reboot, most times, it's back to 640 x 480 with no option to go above that in the screen resolution settings.  *VERY* rarely, it reboots back to 1280 x 1024.

Any idea of how I can force Ubuntu to "stick" to 1280 x 1024?

Thanks in advance.

---

### Post by bodhi.zazen on 2008-05-28
Threads merged.

Please do not start multiple threads on the same issue, it only causes confusion and duplication of effort.

I can not tell from your posts what your question is. From you first post you implied your resolution was fine without your KVM switch, and that with your KVM switch both OS (Windows and Ubuntu) have problems with resolution. My guess is this is a hard ware problem, ie with your KVM.

With your second post you imply the problem is limited to Ubuntu.

Please clarify your question.

1. Is the resolution working without the KVM switch ?

2. If not, what videocard are you using and how are you setting the resolution ?

3. If the resolution settings are working without the KVM, but break with the KVM -> hardware problem for sure.

---

### Post by natanel on 2008-06-07
Ok I have the same problem and by goggling, it look like it a common one

two computers one with XP one with latest Ubuntu and KVM switch

- switching on the XP with KVM no problem with screen resolution
- switching on the Ubuntu with KVM ,the screen resolution couldn't be set more then 640*480 (not so sure about the numbers, but very low resolution)
- taking out the KVM and switching on the bunt all the higher resolutions are enabled
- setting up to high resolution with out KVM and then restart with KVM, the same problem, only low resolution
- there isn't any different if switching with KVM and one of the computer is turned off

I am not expert in that but it look like Ubuntu is not getting the screen resolution with KVM and setting it to default low one.

it will be great if there is any way to force resolution in the Ubuntu

any solution?

---

### Post by dagnabit dang doohickey on 2008-06-07
I don't know if this will help or not, but a few months ago I purchased a LCD monitor to replace a CRT. With the CRT, I was able to boot all of my computers at once without regard to the active port of the KVM switch. Now, with the LCD, I must switch the KVM to each computer before booting, else the resolution will be wrong, requiring me to reset it in the control panel. This behavior happens across the board on all my Macs and PCs.
Something else that was an issue was the refresh rate. If one computer's refresh rate was slightly different than another's, the screens would be shifted and/or have the wrong dimensions. This was easy to fix for Mac and Windows: Select 60Hz in Windows, 59.9Hz in Mac. For Linux, I had to tweak xorg.conf with a modeline. But, I run a very slim Linux system without control panels, so this might be very simple to adjust with gnome/KDE for all I know.

---

### Post by nowforge on 2008-06-07
I also have a problem ..... Ubuntu 8.04 will not allow me to set the resolution of my monitor greater than 800*600. When I first tested Ubuntu (sole operating system), it recognized the video driver and monitor immediately and automatically set iteself to the top resolution (1600*1200). 

As I was testing the software, the screen resolution abruptly changed to 800*600 and would not recognize any commands or hacks to change back.

I reloaded the machine with Xandros (sole operating system) and the screen resolution sets up easily (1600*1200).

I have tried using a KVM switch (one system runs WinXP, one system runs Xandros) and have absolutely no problems (I switch to each system as they boot). When I use Ubuntu, I cannot get a resolution over 800*600 ... hacks don't work.

The hardware works with Xandros ... doesn't work with Ubuntu (this problem is being reported all over the web). Does anyone have any ideas?

I look forward to your help! Thanks

---

### Post by galileux on 2008-10-23
Hi all

I have a D-link DKVM-4U four port USB KVM switch.

It was working fine, switching between  an XP machine (port 1), an Edgy-Eft headless, X-less server, and a Feisty Fawn machine, no problems at all.

I upgraded the Feisty-Fawn machine to Hardy and it no longer holds the resolution through the KVM switch.

If I boot hardy with the monitor directly connected to the machine, all is fine.

If I boot the Hardy through the KVM switch, keyboard and mouse work fine, but the resolution is stuck at 640x480 with no possibility to change it (makes no difference if hardy is on the monitor, while booting, or not).

I noticed that there is bug activity regarding Hardy and KVM switches. My problem only concerns screen resolution, not mouse or keyboard.

I wonder if anyone has had the same problem with hardy, and perhaps found a solution.

Regards
Galileux

---

### Post by galileux on 2008-10-24
Hi all

I seem to have [solved] it "with a little help from my friends" (look for user "dmizer").

I ran

```
sudo dpkg-reconfigure xserver-xorg
```

and answered YES to the question about screen resolution.
On reboot, I was asked to specify a resolution.
I selected "LCD 1280 x 1024".
Rebooted again and it worked fine through the KVM!
Regards!

---

### Post by iridiumcao on 2009-03-21
> **galileux said:**
> Hi all

I seem to have [solved] it "with a little help from my friends" (look for user "dmizer").

I ran

```
sudo dpkg-reconfigure xserver-xorg
```

and answered YES to the question about screen resolution.
On reboot, I was asked to specify a resolution.
I selected "LCD 1280 x 1024".
Rebooted again and it worked fine through the KVM!
Regards!

Hi, galileux,
Does the codes run on host OS or guest OS?

---

