---
title: "Nvidia Geforce GT 730, messed up drivers"
date: 2014-11-20
forum: General Help
---

### Post by eduardoflsantos on 2014-11-20
Hi,

Yesterday my Ubuntu 14.04 was running fine, I played some games and even record it, using RecordMyDesktop from Soft Center.

Today when I turned myu computer on, the login screen was at resolution like 800x600, and when I logged, nothing would happen. Just the cursor and the desktop image were visible, nothing else.

I thought it was some problem with my graphic driver, so I unninstalled it via terminal, because I wanted to install it again.

The problem is, that driver was taken from Nvidia website. So, now I need to either:

- install *something* (some open driver maybe?) that allows me to enter in graphic mode again, so I can go to Nvidia website and install the correct driver again.
or
- install the correct driver directly from terminal.

At the moment I'm not able to enter the login graphic mode, because this appears:
[http://s28.postimg.org/fx1tvydgd/DSC02351_2.jpg](http://s28.postimg.org/fx1tvydgd/DSC02351_2.jpg)

Some ppl trying to help, in Facebook, have told me to install Nvidia311 (or 331?), but it isn't working, and think they are just taking some guesses. So I think I made this even worse :/

Can you help me, please? Thank you.

PS: My PC is an AMD A10-7850K with a Nvidia Geforce GT 730

Edit: 
-Tried to install nvidia-current, still no luck.
-X.org log: [http://s14.postimg.org/6qmza9jip/DSC02356.jpg](http://s14.postimg.org/6qmza9jip/DSC02356.jpg)

---

### Post by Elronius on 2014-11-20
Are you able to access the terminal on startup? (I know it gives you an option to, but do you get to the shell if you select that option?)

Edit: if you can get to terminal (with networking mode enabled), you should be able to wget an NVIDIA install from their website and install it from terminal. I've done that in the past when the kernel NVIDIA installs weren't working and it's ugly but it works. Unfortunately my own machine is down or I'd give you the direct link I used.

---

### Post by eduardoflsantos on 2014-11-20
Hi,

I can get to manual login Alt+F2, isn't that a terminal? xD

I tried to install nvidia-current, but it also doesn't work. I must be missing something in here :/

But I can try that, too. 

/googling how to :P

---

### Post by grahammechanical on 2014-11-20
Ubuntu has an open source video driver which it uses as a default. When we install a proprietary video driver the open source driver is de-activated but not removed from the system. In the case of Nvidia graphic adapters the open source video driver is called Nouveau. At the Grub boot menu, select Advanced Options for Ubuntu and then select Recovery mode. At the recovery menu select Resume. That should load to a desktop using an open source video driver call llvmpipe. To get to a Linux command prompt use Ctrl+Alt+F1. To install a standard proprietary video driver from the command line use ```
ubuntu-drivers autoinstall
```

---

### Post by zircon_34 on 2014-11-20
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
perhaps my thread may help you, though you should select the right driver for your card...

---

### Post by eduardoflsantos on 2014-11-20
> **grahammechanical said:**
> Ubuntu has an open source video driver which it uses as a default. When we install a proprietary video driver the open source driver is de-activated but not removed from the system. In the case of Nvidia graphic adapters the open source video driver is called Nouveau. At the Grub boot menu, select Advanced Options for Ubuntu and then select Recovery mode. At the recovery menu select Resume. **[COLOR=#000000]That should load to a desktop using an open source video driver call llvmpipe[/COLOR]**. To get to a Linux command prompt use Ctrl+Alt+F1. To install a standard proprietary video driver from the command line use ```
ubuntu-drivers autoinstall
```

Hi,

I did what you suggested, but I still get this screen: 
[http://s28.postimg.org/fx1tvydgd/DSC02351_2.jpg](http://s28.postimg.org/fx1tvydgd/DSC02351_2.jpg)

:/

---

### Post by eduardoflsantos on 2014-11-20
> **zircon_34 said:**
> [http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
perhaps my thread may help you, though you should select the right driver for your card...

Hi,

I have installed the correct driver before, but yesterday things seems to have stoped working, out of nowhere. I really can't explain how it happened (some ppa update?). I had the same problem as you, my system couldn't find my driver, so I had to get it from Nvidia website. I want to try to install it again, yes, but for now I can't even login in the graphic mode, to get it.

---

### Post by pqwoerituytrueiwoq on 2014-11-20
since you installed the nvidia driver from there website every time your kernel updates you have to reinstall it (that is probally your issue)
nvidia install a un-install application i think it is nvidia-uninstall

---

### Post by zircon_34 on 2014-11-20
you must be able to download the driver in text mode. perhaps the best bet is to add a ppa as suggested from others in the thread mentioned earlier.

Hope you manage to fix it, good luck!

---

### Post by zircon_34 on 2014-11-20
> **pqwoerituytrueiwoq said:**
> since you installed the nvidia driver from there website every time your kernel updates you have to reinstall it (that is probally your issue)
nvidia install a un-install application i think it is nvidia-uninstall

```
sudo apt-get remove --purge nvidia-*
``` should do it....

---

### Post by pqwoerituytrueiwoq on 2014-11-20
> **zircon_34 said:**
> ```
sudo apt-get remove --purge nvidia-*
``` should do it....

> **eduardoflsantos said:**
> The problem is, that driver was taken from Nvidia website.
op did not instal the driver using apt, but nvidia .run file

---

### Post by eduardoflsantos on 2014-11-20
> **pqwoerituytrueiwoq said:**
> op did not instal the driver using apt, but nvidia .run file

Actually, it kinda worked. Maybe because I tried to install other drivers since I got into this problem.

I'm now in graphic mode, although in a very very bad resolution. Check out the print:

[http://s27.postimg.org/s0lo5os37/Captura_de_ecr_de_2014_11_21_04_38_43.png](http://s27.postimg.org/s0lo5os37/Captura_de_ecr_de_2014_11_21_04_38_43.png)
xD

So, what is the best way to install my driver, that is not available in 3ºparty drivers of Ubuntu update system (or whateve it is the name xD)? I don't think I'll download the file from Nvidia website again.[-X

---

### Post by pqwoerituytrueiwoq on 2014-11-21
if your card is not very new just open [FONT=courier new]software-properties-gtk[/FONT] and grab it in the additional drivers tab
if you need a newer driver, add the xorg edgers ppa then do the above
```
sudo apt-add-repository ppa:xorg-edgers/ppa -y && sudo apt-get update
```

---

### Post by eduardoflsantos on 2014-11-21
It's a cheap card, but I think it's new, only has some months.

I did that, but I'm still on 800x600. Ubuntu gives me this warning (my translation into english):
Unable to apply the saved configuration to the screens.
None of the selected mode was compatible with the possible modes:
Trying modes to CRTC 382
CRTC 382: trying mode 640x480@73Hz with exit at 800x600@0Hz (passage 0)
CRTC 382: trying mode 640x480@73Hz with exit at 800x600@0Hz (passage 1)

And in the additional drivers, I have these, now:
[http://s1.postimg.org/cqa5q5s67/add.png](http://s1.postimg.org/cqa5q5s67/add.png)

---

### Post by eduardoflsantos on 2014-11-21
Hi,

After changing the driver to the nvidia, again, in 3rd party drivers tab, things got even worse, I was unable to login in graphic mode and in Alt+F2 mode. System just showed my a underscore _ that kept flashing in the screen. I had to make a fresh install :(

Anyway, thank you to everyone that spend their time helping me here ;)

---

### Post by pqwoerituytrueiwoq on 2014-11-21
i don't mean how long you have had the card, i mean how long that model has been on the market
you should use the 331 driver or the 343 beta driver

if you are still stuck in 800/600 you have not removed the nvidia driver you installed from nvidia
if you type nvidia and hit the tab key a few times in your terminal you should find a command that will remove that driver

---

### Post by eduardoflsantos on 2014-11-21
Hi [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458"),

I think you missed my last message, we posted at the same time ;)

I've downloaded nvidia-331-updates from Ubuntu software centre, I think it's good so far. The card is a nvidia GForce GT 730, I think it was launched in July 2014.

---

### Post by pqwoerituytrueiwoq on 2014-11-21
ur right i did miss that
anyway long story short installing from nvidia's site is advanced users only, they really should mention the proper way to install the drivers as the 1st thing a new ubuntu users will do is go there and try to install itr from there website like they had to do in windows

---

