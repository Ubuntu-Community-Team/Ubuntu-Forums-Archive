---
title: "Computer won't boot from hard drive"
date: 2006-12-10
forum: General Help
---

### Post by lou1998 on 2006-12-10
My computer gets past post and just sits with a blank screen.  I can boot to a CD and I can access my hard drives.  I tried reinstalling GRUB and also restoring the MBR, but nothing has worked.  Any ideas?

---

### Post by DaveBorealis on 2006-12-10
> **lou1998 said:**
> My computer gets past post and just sits with a blank screen.  I can boot to a CD and I can access my hard drives.  I tried reinstalling GRUB and also restoring the MBR, but nothing has worked.  Any ideas?

Hello,

My guess is that you're set at a setting your video card/monitor can't handle.  Can you get to the grub prompt during boot up?  If so, try the following parameter:
```
vga=771
```
I think that should be doable for most setups.  Then you can play around with '/etc/X11/xorg.conf' to get your X working.

Dave

---

### Post by r3t0 on 2007-01-12
I have exactly the same problem as lou1998:

Using Edgy and Software RAID1 I cannot boot anymore. After the BIOS I see a blinking cursor (grub?) and... nothing. just that blinking cursor.

This is what I did last before the reboot:
- installed all updates: I went through every update. Most of them where gnome-applet related, but I cannot remember all. I definitely updated xorg and nvidia drivers two days ago, but the system booted fine twice since!

- Did the reboot and now I cannot even see grub posting anything to the screen.

Any help is much appreciated!

reto

Some more info:
- Asus P5B mainboard
- Software RAID1 with 2x 320gb samsung hdd
- Asus Geforce 7600 GL Graphics
- 2gb RAM
- Core2duo E6600

---

### Post by r3t0 on 2007-01-12
sorry, me again with updates:

I disconnected on of the drives and ubuntu boots. BUT it boots into a state which is about as old as the system was right after the installation wrong background, wrong theme in gnome etc. a lot of Files are missing (in my /home/ dir).

So, I guess the most recent data is on the other disk and the raid didn't really work as it should.
How do I make sure the disk with the old data sync to the one the the recent data and not vice versa? I feel kind of helpless right now...

---

