---
title: "Computer lags, mouse freezes"
date: 2020-04-02
forum: General Help
---

### Post by claven123 on 2020-04-02
My desktop lags and slows, mouse freezes and sputters.  This seems to happen when libreoffice is open and when many things are happening on screen, or when programs are opening.  It's hard to figure out what specifically is happening.  I feel it started after I upgraded to 19.10 (upgraded from 19.04).

I have a Dells Desktop Inspiron 3847 (Inspiron 3847)
Ubuntu 19.10 dual boot with windows
Intel 3.10
Gnome: 3.34.2
64 bit
1.0 TB

Dennis

---

### Post by daniewicz on 2020-04-02
How much RAM? 
Does the desktop work well under Windows?
What version of Windows?
Integrated or discrete video card?

---

### Post by NM5TF on 2020-04-02
> **claven123 said:**
> My desktop lags and slows, mouse freezes and sputters.  This seems to happen when libreoffice is open and when many things are happening on screen, or when programs are opening.  It's hard to figure out what specifically is happening.  I feel it started after I upgraded to 19.10 (upgraded from 19.04).

I have a Dells Desktop Inspiron 3847 (Inspiron 3847)
Ubuntu 19.10 dual boot with windows
Intel 3.10
Gnome: 3.34.2
64 bit
1.0 TB

Dennis
like the last poster asked, how much RAM do you have ??
also, does the mouse work correctly under Windows ??

if you have inxi installed, open a terminal & type this 

```
inxi -I
```

post the output in your reply, using code tags is preferred

if you don't have inxi, use sudo apt-get install inxi and then repeat the above...

1 more thing to consider is your mouse cable, if it has 1...just had to replace my mouse due to a bad cable that was causing
the very symptoms you are seeing...

tommy

---

### Post by claven123 on 2020-04-06
Yes, it works fine under windows.
I have 3.8 RAM (from the About screen)

It seems like the whole CPU bogs down and is represented by the mouse activity.  Or, some process is running the background, I've looked at the CPU usage and doesn't seem to be anything abnormal.

I'll install the inxi and run that when I can.

Thanks,

D

---

### Post by claven123 on 2020-04-09
inxi -I
Info:
  Processes: 236 Uptime: 3d 2h 58m Memory: 3.76 GiB used: 2.45 GiB (65.1%) 
  Shell: bash inxi: 3.0.36

Dennis

---

### Post by leok2 on 2020-04-10
Is this then resolved?

---

### Post by claven123 on 2020-04-10
Nope, I've no suggestions on how to improve or make changes. 

Thanks thus far.

D

---

### Post by CelticWarrior on 2020-04-10
> **claven123 said:**
> Nope, I've no suggestions on how to improve or make changes. 

Thanks thus far.

D

The reason for that is mainly because you haven't provided any useful hardware specifications, especially the graphics because in all likelihood it needs drivers. BTW, the command  ```
inxi -I
``` (with an uppercase "i") is exactly for that.

---

### Post by claven123 on 2020-04-10
dennis@dennisDesktopDual:~$ inxi -I
Info:
  Processes: 224 Uptime: 3d 23h 20m Memory: 3.76 GiB used: 2.54 GiB (67.4%) 
  Shell: bash inxi: 3.0.36 

That is the output of the request (same as above).  I'm more than happy to provide any information that I can to help you help me.  Let me know what you need and I will provide it.  I'm very grateful for the help, I've done all I've been asked :)

D

---

### Post by CelticWarrior on 2020-04-10
Please post the result of ```
inxi -G
```

---

### Post by dragonfly41 on 2020-04-10
What you might find useful is a dashboard to inspect resources. You can do this through command line but I recommend this utility.

[Stacer]("https://github.com/oguzhaninan/Stacer").

You can install using these commands ... 

[COLOR=#b22222]Later edited ppa: below due to a typo error. [/COLOR]
[COLOR=#24292E][FONT=SFMono-Regular]
[/FONT][/COLOR]sudo add-apt-repository ppa:oguzhaninan/stacer -y
sudo apt-get update
sudo apt-get install stacer -y


I would look at Resources (from menu) and look for where there is heavy usage.  CPU or RAM.

Also try running browser without a multitude of tabs open

---

### Post by claven123 on 2020-04-10
dennis@dennisDesktopDual:~$ inxi -G
Graphics:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics 
  driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel Haswell Desktop v: 4.5 Mesa 19.2.8

---

### Post by CelticWarrior on 2020-04-10
Post #11 says it all. There's nothing unusual in your hardware but you need to understand its limitations, namely RAM.

---

### Post by claven123 on 2020-04-10
I understand the RAM, tabs etc... however, this ran perfectly before the upgrade to 19.10.  Then after I have all the issues.  I may be able to associate this to LibreOffice, which also upgraded with Ubuntu upgrade as well.  

CAN an upgrade to 19.10 dramatically change the RAM requirements?  To the point the performance suffers?  I'm sure I can add some RAM, but.   I was going to wait until the next version comes out and see if that makes a difference. 


Dennis

---

### Post by claven123 on 2020-04-10
FYI:
Cannot add PPA: 'ppa:~guzhaninan/ubuntu/stacer'.
ERROR: '~guzhaninan' user or team does not exist.

---

### Post by mörgæs on 2020-04-11
> **claven123 said:**
> 
CAN an upgrade to 19.10 dramatically change the RAM requirements?  To the point the performance suffers? 

In-place upgrades can always break a system. It's not specific to 19.10. 

Fresh install every time.

---

### Post by dragonfly41 on 2020-04-11
> [COLOR=#000000]FYI:[/COLOR]
[COLOR=#000000]Cannot add PPA: 'ppa:~guzhaninan/ubuntu/stacer'.[/COLOR]
[COLOR=#000000]ERROR: '~guzhaninan' user or team does not exist.[/COLOR][COLOR=#000000]
For some reason when I paste the PPA from the stacer website a smiley icon appears.

See original post above when direct copying from web site. Somehow :o string ("colon followed by o") translates into smiley.

I suggest that you refer to Stacer website and use installation instructions there.

They do work for me. And Stacer is my daily tool.






[/COLOR]

---

### Post by claven123 on 2020-04-11
Attempted to install from apt get, failed. 

I think I'll attempt a fresh install when 20.04 comes out in a few weeks. 

D

---

### Post by dragonfly41 on 2020-04-11
I don't know why PPA doesn't work for you. Another method is to download the *.deb file [from here]("https://sourceforge.net/projects/stacer/files/") then use Gdebi to install.

---

### Post by claven123 on 2020-04-15
Two things, I was able to install stacer, works well. using getdebi.

I ordered 16 of RAM and it came in today (up from 4).  Kinda overkill, but why not, right.  I installed and the problem is now gone. 

Thanks all for the assistance.


D

---

