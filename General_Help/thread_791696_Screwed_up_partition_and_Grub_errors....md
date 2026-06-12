---
title: "Screwed up partition and Grub errors..."
date: 2008-05-12
forum: General Help
---

### Post by Lilibette on 2008-05-12
Yeah, I made a major boo-boo.

I had Windows Vista on my computer and it went ka-put. I don't know what happened, but suddenly BOOTMGR wasn't found. Sooo, I installed Ubuntu.

Everything was running fine, and then I decided I wanted to get Windows back so that I can play some games I miss. Anyway, I used Gparted to try and partition my hard drive and now Grub gives me a Code 22 error and whenever I put the Windows install disk in, it tries to install it on a 118mb partition. :(

I have no clue what I did, why I did it, or how to fix it.

Please have mercy on a young lady with a broken laptop and broken heart.

Specs:
Gateway ML6720
Intel Pentium Dual Core T2310 / 1.46 GHz 
1GB RAM

Thanks guys. 
:confused:

---

### Post by jerrallan on 2008-05-12
Boot your Ubuntu Live CD[the Cd you used to install Ubuntu] Go to system>administration>partion manager and report the partitions.
Your computer bios needs to be set to boot the CD first.

I don't suppose you have a windows cd?

Depending on what the partition manager shows, you may be able to restore grub or mbr by Super Grub disk, if you can get internet access and are able to burn a CD.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Lilibette on 2008-05-12
Oops

---

### Post by Lilibette on 2008-05-12
I do indeed have the Live CD, and I do have a Windows XP cd.  I also have downloaded SG Disk, so all I have to do now is go home and try to work on it...

I'll report tomorrow with what happens.  *CROSSES FINGERS*

---

### Post by jerrallan on 2008-05-12
Don't do anything with that XP CD.  You have Vista. Bad things might happen.

Boot the Ubuntu disk first and check the partitions

You can do this by going to Applications>Accessories>Terminal
type in sudo fdisk -l ,and report the results.

There is a way to manually restore using terminal commands, but on LIVE CD none of the how to's worked for me.  If your Windows boot record is repairable, The best thing to do would be to download Super grub disk.  It worked for me. I have Windows XP by the way.

I am guessing you can get internet access because you are responding to me.

Do you want Ubuntu back and running, besides your Vista?

---

### Post by Lilibette on 2008-05-14
> **jerrallan said:**
> Don't do anything with that XP CD.  You have Vista. Bad things might happen.

Boot the Ubuntu disk first and check the partitions

You can do this by going to Applications>Accessories>Terminal
type in sudo fdisk -l ,and report the results.

There is a way to manually restore using terminal commands, but on LIVE CD none of the how to's worked for me.  If your Windows boot record is repairable, The best thing to do would be to download Super grub disk.  It worked for me. I have Windows XP by the way.

I am guessing you can get internet access because you are responding to me.

Do you want Ubuntu back and running, besides your Vista?

What I was initially *trying* to do was get rid of Ubuntu altogether and install XP, which I know is ridiculous now and I went in the total wrong direction and made things worse for myself.

I'm in the process of reburning my ubuntu disk so that I can give you the info from fdisk.

Last time I attempted to run the Live CD I had, the screen just lit up with tons of errors and they didn't seem to end.  I had to force shut down to get it to stop displaying errors and Ubuntu never loaded. :(

So... 5 mins and I'll get the info... hopefully.

---

### Post by az on 2008-05-14
Grub gave you the error because you changed the partition table and didn't tell grub.  Grub was looking for the second stage of the bootloader in the wrong spot.

If you only want to get rid of everything and start from scratch, you just need to start with an empty partition table.  Boot the Ubuntu live cd and use the partitioning tool in the administration menu to delete all partitions on your disk.

Once you have done that, the XP install disk will be able to install.

Once you have installed XP, you can install Ubuntu beside it.  The ubuntu installer will shrink the XP partition, so you don't have to worry about it right now.

---

### Post by Lilibette on 2008-05-14
Well when I tried to run the live cd, I got the errors again.  Line after line after line reading:

```
Buffer I/O error on device sr0, logical block 172435
```

And it goes on and on, different numbers every time, but always sr0.

Any clue as to what is going on?

---

### Post by az on 2008-05-14
You have a faulty optical drive.

Can your laptop boot from usb?
[http://ubuntu-rescue-remix.org/node/21](http://ubuntu-rescue-remix.org/node/21)

---

### Post by Lilibette on 2008-05-14
> **az said:**
> You have a faulty optical drive.

Can your laptop boot from usb?
[http://ubuntu-rescue-remix.org/node/21](http://ubuntu-rescue-remix.org/node/21)


It can, but I don't have a USB stick.  Argh!  ](*,)

Other disks seem to work just fine in my drive... even if I put in Gparted or Damn Small Linux live cd (which I have handy on me atm).

---

### Post by jerrallan on 2008-05-14
well, keep us posted.

---

