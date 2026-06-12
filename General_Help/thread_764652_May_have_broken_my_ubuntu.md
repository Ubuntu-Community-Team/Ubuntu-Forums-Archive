---
title: "May have broken my ubuntu"
date: 2008-04-24
forum: General Help
---

### Post by rock122 on 2008-04-24
So I installed Ubuntu 7.10 about 3 weeks ago and so far a loving it... until tonight that is. I went to administration > updates(or whatever it says, basically preparing to upgrade my version) It had some odd 215 security updates or so, after downloading them all it began the install. During this I was stupidly using firefox when all of a sudden everything just stopped responding. The update window was about 1/4 of the way into installing when this happened. After waiting an hour or so I decided to restart the computer.

Upon restart into ubuntu it tells me it can no longer detect my video driver and default resolution will be used. The login screen then appears, after logging in all that happens is the orange background remains and nothing else is on the screen.

Any help with getting this working again would be great, thanks!

-Dell Inspiron E1505,
-Dual booted with Vista which is currently working
-Nvidia Graphics card in the laptop

---

### Post by russo.mic on 2008-04-24
So,  first things first,  lets make a copy of your xorg.conf.  from your recovery terminal execute:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

Next, lets rebuild it. execute:

sudo dpkg-reconfigure -phigh xserver-xorg


Select the revelant options, and type startx. If X starts okay, then when you quit, it'll probably just go back to the terminal.  type sudo reboot now, and we should be in happy land.  let us know of your results!

Russo

---

### Post by Tatty on 2008-04-24
Considering you want to update to hardy anyway, the easiest thing to do is probably to

a) boot into a live CD
b) back up anything you dont want to lose
c) do a fresh hardy install tomorrow

**Edit:** Probably best to try russo's suggestion first.
**Edit Edit** were you doing a distro-upgrade or just standard security updates?

---

### Post by ibuclaw on 2008-04-24
Also, check your hardware.

One of the main reasons why a screen might freeze is because of the graphics card overheating.

Check your BIOS settings to make sure that your graphics fan, etc. is set to a reasonable level. (Don't over-do it)

Regards
Iain

---

### Post by rock122 on 2008-04-24
When I type sudo dpkg-reconfigure -phigh xserver-xorg

all that happens is i get this message

"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20080424103230"

Any help is appreciated

---

### Post by rock122 on 2008-04-24
Ok so after doing the command I just mentioned my resolution got fixed but when I enter my login info and hit enter it still just hangs at the orange background between login screen and desktop.

---

### Post by martinic on 2008-04-24
I have a very similar problem and have tried doing these things suggested here, but when I enter sudo ... it says something like Root martin-desktop not recognised so I can't actually enter any commands.

---

### Post by Raptor45 on 2008-04-24
Once you hit the login screen, press ctrl-alt-f1 to switch to a terminal. Login, then do "sudo apt-get update", "sudo apt-get upgrade". Hopefully that should finish the upgrade process, if not you may be in a tough situation.

---

### Post by martinic on 2008-04-25
OK so I did that but it told me I couldn't, so I did (I think) 
dpkg --reconfigure -a
which started to work but then said something like dpkg: too many errors

It's starting to look like in needs a clean install methinks, unless anyone has any other suggestions.

---

### Post by Saya on 2008-04-25
> **martinic said:**
> OK so I did that but it told me I couldn't, so I did (I think) 
dpkg --reconfigure -a
This (with sudo) is what usually works for me when I get a power failure or such during updates. Log in to a safe xterm session and try it from there.

---

