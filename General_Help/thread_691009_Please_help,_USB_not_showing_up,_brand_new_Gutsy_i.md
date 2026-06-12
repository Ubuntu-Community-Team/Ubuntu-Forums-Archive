---
title: "Please help, USB not showing up, brand new Gutsy install."
date: 2008-02-08
forum: General Help
---

### Post by ogwilson on 2008-02-08
Just installed Ubuntu 7.10 GG, installed all updates, etc, but my USB flash stick isn't being recognized. I've had GG before and it recognized the stick just fine. Also, what's this hda1 on my desktop? It has nothing in it and I don't know what it's for.

Anywho, can anyone please help?

PS: This is a different PC than the one in sig:

Emachines T6414
1.5 gigs of Ram
AMD Athlon 3200+ processor
160gig harddrive
Integrated ATI Radeon 200 128megs shared graphics.

---

### Post by Pelham123 on 2008-02-08
Dont mean to ask the obvious, but does the stick *work*? ie - any LED lights activate when plugged in?

With the usb stick plugged in, what is the output of terminal command 'lsusb'?

---

### Post by danwood76 on 2008-02-08
> **ogwilson said:**
> Also, what's this hda1 on my desktop?


That might be your flash drive.

can you post the output of these two commands in terminal:
```

lsusb
and
sudo fdisk -l
```

it might be that you need to mount the disk manually.

regards,
Danny

---

### Post by ogwilson on 2008-02-08
I got it working guys. Um, embarrassing story actually. I accidentally tried to format the USB drive as a swap partition when I was installing Ubuntu last night(i was mega tired.) It wasn't until i plugged it into a windows machine that i finally figured out what'd happened. Anywho, I reformatted, lost all my precious data that is not backed up, and all is well. Thanks anyway guys.

---

