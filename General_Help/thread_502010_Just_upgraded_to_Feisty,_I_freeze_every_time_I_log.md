---
title: "Just upgraded to Feisty, I freeze every time I log in as something other than root"
date: 2007-07-16
forum: General Help
---

### Post by Phayder92889 on 2007-07-16
I dunno what all you need to help diagnose problems, but I just automatically updated to Feisty from Edgy.

If I log in normally, I get about 5 minutes of 'on' time, then it grinds to a halt. Going the long way round with GRUB, I can log in as root and it seems to work just fine (I haven't gone for longevity, I've just fixed a few oddities in fstab and xorg.conf from updating things manually, then having them automatically updated. (I think. The error log said a few things about changes in lines that I hadn't touched that weren't working)

Very frustrating, please help?

---

### Post by grahams on 2007-07-16
If you aren't getting errors and you don't have much memory you may want to check if your swap is turned on with 'free' or 'top'. I lost swap in the upgrade as the UUID of the swap partition changed but /etc/fstab didn't update.

---

### Post by Phayder92889 on 2007-07-17
I have a full gig of memory, and I don't know where to look for error messages.

---

### Post by grahams on 2007-07-18
With a Gig you shouldn't see a freeze even without swap. 

Try logging is as root and use as you would normally. If the system is stable for a long time, try to see what is different, i.e. do you use compiz/beryl as a regular user but not as root, it may indicate a graphics driver issue. If things also lock up when logged in as root, run dmesg and look for errors (assuming you can run anything at this stage). Also scan thru the syslog files under /var/log/ 

Is there a certain app you always have open when you get a freeze? 

If all else fails  the few times I've suffered similar issues it been down to a lousy fglrx  graphics driver. Edit your xorg.conf and choose the vesa driver and restart X (or reboot), if that stops the hangs try updating the driver or use the open source ati driver (if you can)

good luck

---

### Post by Phayder92889 on 2007-07-19
I've been up for over 2 days as root. I've been running all the same programs as I usually do, and I haven't installed Beryl/Compiz on this unit yet.

It freezes pretty regularly, regardless of what I'm doing; if I let it idle on the login screen, it'll lock up there, too.

Outside of that, I dunno what to say/think, other than I'm in the same boat as at least 30 other people on this forum.

---

### Post by grahams on 2007-07-23
The few times I've seem freezing issues like this it been a video driver issue. 

Although the graphics will perform really poorly try editing your /etc/X11/xorg.conf file to use the vesa driver rather than the Nvidea, ati or which ever driver you're currently using.  If you do not get freezes with vesa, see if there is a update for the driver or a better driver (open source ATI driver vs. flgrx etc.)

---

