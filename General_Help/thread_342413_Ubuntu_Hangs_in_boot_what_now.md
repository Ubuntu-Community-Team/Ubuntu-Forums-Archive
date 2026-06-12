---
title: "Ubuntu Hangs in boot what now?"
date: 2007-01-20
forum: General Help
---

### Post by jloehrlein on 2007-01-20
Ubuntu (edgy) starts to load and goes through most of the process but right when it should show the login screen it just shows black.

This problem started right after I setup gaim. I noticed none of my programs would start and restart button on the gui wasn't reponding so I had to cut the power and reboot, that's when this started.

I can get into recovery mode via grub, but I've just started using linux and have no idea what to do.

Some help would be awesome

---

### Post by K.Mandla on 2007-01-20
If it locks up at a black screen, you might try pressing ALT+F2 or another F key, to see if you can find a console log that shows any error.

If you can boot into recovery mode and you think GAIM might be the problem, you can uninstall that from the command line ... but to be honest, I'm not sure what GAIM would have to do with the rest of the system misbehaving.

Did you install any new drivers, or system services?

Is this a custom-built machine? Could you be having cooling problems?

---

### Post by jloehrlein on 2007-01-20
I tried reinstalling xserver-xorg with:

sudo apt-get install xserver-xorg

but it asks me if I want to install the adobe flash plugin, tries to reguardless of whether I say yes or no, fails to download and stops reinstalling xserver.

I hate to ask but is there some sort of repair install option (like windows)?

---

### Post by jloehrlein on 2007-01-20
> **K.Mandla said:**
> 

Is this a custom-built machine? Could you be having cooling problems?

Yeah it's a new custom machine but I'm dual booting windowsXP and that still works.

---

### Post by jloehrlein on 2007-01-20
> **K.Mandla said:**
> If it locks up at a black screen, you might try pressing ALT+F2 or another F key, to see if you can find a console log that shows any error.


What does alt-f2 do and when should I use it? I tried banging the f keys during bootup. Alt and something in the f9 to f12 range showed about 7 lines of text. The last of which was "checking file system" or somethign like that. Then it went black.

Like I said recovery mode seems to be fine.

---

### Post by jloehrlein on 2007-01-20
I used the live cd to remove "quiet splash"

It gets through the part where you see the ubuntu progress bar with blue text under it. It loaded the hardware drivers, network config, etc.. 

The last thing I saw listed said something about the kernal, but it was only on screen for maybe a fifth of a second. Then it looks like it is about to start the gui, there is a flashing cursor in the upper left hand corner. The cursor goes away, the harddrive chugs for a second or so, then goes quiet and I only have a black screen.

---

### Post by jloehrlein on 2007-01-20
bump

---

### Post by cracker on 2007-01-20
For future reference, cutting the power should be a VERY LAST resort. There are several things you can do if X crashes. First, press CTRL+ALT+F1 to go to a text terminal. Here, you can kill processes you think might be locking up X. If you don't know what's causing it, or can't figure it out, press CTRL+ALT+BACKSPACE to restart X. If X doesn't respond, or you still have problems, switch to a terminal by pressing CTRL+ALT+F1, and press CTRL+ALT+DEL to reboot the system.

Now, since you cut the power, it's possible files were corrupted. First, try to reconfigure X by running the following at a terminal:

sudo dpkg-reconfigure xserver-xorg

Just accept the defaults if you don't know what to put in. If the system still doesn't work, it's beyond my ability, and I'd suggest you try and reinstall if you haven't got any important data or configuration set. If a liveCD that worked before no longer works, then you likely have damaged hardware.

---

### Post by jloehrlein on 2007-01-21
Yep x was all messed up, thanks for the info.

---

