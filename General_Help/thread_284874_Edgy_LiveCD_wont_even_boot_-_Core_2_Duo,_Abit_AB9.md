---
title: "Edgy LiveCD wont even boot - Core 2 Duo, Abit AB9"
date: 2006-10-26
forum: General Help
---

### Post by v8YKxgHe on 2006-10-26
Hey,

Well after waiting hours for Edgy to be released I downloaded it right away, burnt the disc ( well, 5 of them ... it just wouldn't burn to start with on the CD's I had so I had to get some more ) 

I turn off my PC, unplug my WinXP hard drive and plug in my spare hard drive ready for Ubuntu Edgy. I select "Start or Install Ubuntu" and all I get is either:

- Gets suck at around 8% loading Linux Kernel
- Error loading boot disk, or something similar to that error message, which then tells me to reboot.

So I restart and run the check on the disk to make sure it's all ok. All I get is a fugly, and I mean fugly Ubuntu logo with a little progress bar going back and forwards for ever, with my CD Drive spinning up and down in regular intervals. I left it for 40 mins doing the check but it just got no where. 

There is no way I can even boot the live CD, it just doesn't work. Here are the specs of my new machine:

Intel Core 2 Duo E6600
Abit AB9
GeIL 1GB ( 2x512 ) PC5300
2xSATA 2 120GB Western Digital Hard Drives
ATI X800XT

So, after waiting months for Edgy and 2-3 hours of downloading/burning CD's I can't even install it, I can't even load the LiveCD. 

Can anyone help me at all?

---

### Post by v8YKxgHe on 2006-10-26
I have managed to boot into the LiveCD and am currently installing Ubuntu Edgy now. What I had to do was enter the BIOS on my Abit AB9 and disable some things ( like USB controllers and I _think_ an IDE Controller but I'm not sure, just disable everything :p ) hopefully it will work once installed.

Edit: I also got "Unable to boot cd" and got told to restart, after restarting I no longer got the error message and was able to begin loading Ubuntu Edgy

---

### Post by v8YKxgHe on 2006-10-26
Well actually seems like I was wrong. I managed to install Ubuntu Edgy but now I can't boot from it. Any help would be appriciated

---

### Post by pasuuna on 2006-12-13
I also own an Abit AB9. Neither the Ubuntu Edgy (64-bit) live-CD or the installed Ubuntu system will boot if I have legacy keyboard support turned on from the BIOS.

"USB keyboard support" will have to be set to "OS" (not "BIOS") for Ubuntu to boot. I hope this helps.

---

### Post by v8YKxgHe on 2006-12-13
I gave up and brought a new motherboard ( Abit AW9D ) after Gentoo, Arch, Debian, Ubuntu, and FC6 would not work.

---

### Post by jimbob on 2006-12-13
There have been problems experienced (including mine) trying to install from the Live CD.

Suggest you download and burn the alternate (text mode) CD and try that.

Worked for me ...

EDIT: Your solution seems to be a bit expensive.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by v8YKxgHe on 2006-12-13
> **jimbob said:**
> There have been problems experienced (including mine) trying to install from the Live CD.

Suggest you download and burn the alternate (text mode) CD and try that.

Worked for me ...

EDIT: Your solution seems to be a bit expensive.
&#65279;

I had downloaded the Alternate CD and tried that yet nothing worked. I've been trying on and off since Edgy was released to get it to work, and after trying several other distro's that still did not work, I gave in. May have been expensive but at least I can use my favorite OS :KS

---

### Post by Watter on 2006-12-21
I had trouble with a similar configuration. A new motherboard wasn't an option I was going to go with in my case. 

[http://ubuntuforums.org/showthread.php?t=313366](http://ubuntuforums.org/showthread.php?t=313366)

I never did find a solution for getting Edgy installed. I'm using Feisty Fawn instead and let me tell you, it sucks using an alpha. It's a toss up on a day by day basis whether or not I'll be able to log in. I may have to use OpenSuse until Fesity is released.

---

### Post by rianquinn on 2007-02-19
I have the same problem. I'm waiting for Fiesty, while I currently use Vista. Sucks though, I'd rather use Ubuntu.

---

