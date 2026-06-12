---
title: "Grub won't load"
date: 2008-03-09
forum: General Help
---

### Post by windowsh8r on 2008-03-09
I recently removed and reinstalled Open Office to allow me to view ppt slides.  I did it through synaptic, and now if my computer is off for more than 8 hours or so, when I turn it on, it won't get to the grub loading line.  The _ just blinks and nothing.  I can turn it off and restart it but the same.  If I start up a live CD and then try to mount the HD, it says mount refused, but when I shut down, I can reboot and everything works fine through the hard drive.  Also, if I go into the  BIOS setup and exit, grub loads and everything works.  If I turn it off and come back to it in a couple hours it is fine.  I have had no problems prior to removing/reinstalling Open Office.  
My system is a Compaq presario with AMD processor, I am running Feisty.  No windows, no partitions.

Thanks

---

### Post by matty_b_1000 on 2008-03-09
I have the exact same problem with an Intel Dell Dimension 3000. If I wait long enough, the GRUB menu shows, and I can boot, but if I select Windows, the XP loading screen appears, then the blinking cursor of doom. If I wait long enough (~5mins), then Windows loads.

Anyone?

---

### Post by windowsh8r on 2008-03-11
I do not have windows on this computer, so if I just wait long enough, I get a media device failure, like the HD is not there.

---

### Post by retrow on 2008-03-11
I had a similar problem after there was a Kernel update. There were multiple entries in menu.list for Ubuntu with 3 different kernel options. By default its the first entry that gets select after timeout, but if something is amiss it just keeps on blinking (and I didn't have enough patience to watch it blink for more than 2 minutes).

When you get the grub screen hit 'Esc' and try choosing a different kernel. If it works with the new selection, make that your default by editing your menu.list.

Your problem might be something entirely different, but this is what had happened on my end.

---

### Post by windowsh8r on 2008-03-12
Where is menu.list?  I did a search for it and it is not showing up.

---

### Post by TrashmanL on 2008-03-12
Just today I started having problems with GRUB. I don't use GRUB to load windows, so I can still boot Windows. (I use BootMagic to load windows on hda, or boot hdb which will start grub) I have an old emergency boot disk that I'm going to try  I can't try any other options right now. When I try to load GRUB it just says:

GRUB

on the screen. Nothing else. The grub menu doesn't come up, anything, it just sticks there. I'll try some of the rebooting options. Big problem... if I can't get Linux to load, I can't access any of the grub settings to begin with! I guess another option is to use the live CD to boot then mount my hdb partitions.

I'm about to try those, but figured I'd post in case anyone knows exactly what would cause this. Recently, I have done the regular updates, and a few GTK, OpenGL and Glide Libraries from Synaptic.

---

### Post by unutbu on 2008-03-12
windowsh8r, to answer your question, menu.lst is at /boot/grub/menu.lst. It is the file that tells grub how to boot any OS's that may be on your hard drive partitions.

Your machine's symptoms are bewildering, and I doubt I can help you all the way, but someone here might get some ideas if you post the output to the following:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by TrashmanL on 2008-03-12
OK. I'm up and running. I had to boot to the Feisty Install CD, go to rescue mode, and reinstall GRUB. If nothing else works, you may want to try that. I'd probably recommend you do an fsck of your root partition though, too. I should've done that first, now that I think about it. After I reinstalled GRUB and got Ubuntu to load, the fsck on boot found problems and fixed them.

---

