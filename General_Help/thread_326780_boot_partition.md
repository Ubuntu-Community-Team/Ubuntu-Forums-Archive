---
title: "/boot partition"
date: 2006-12-28
forum: General Help
---

### Post by ghepardo on 2006-12-28
Is a boot partition really necessary? I installed ubuntu with the root aprtition, a swap one and a home one. Should I reinstall with a boot partition too?
Also, I need to reinstall winxp, so I will need to restore grub. In this guide:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
the example is with a boot partition.
The absence of this partition in my system will compromise the restore of grub using the above method ?

---

### Post by kidders on 2006-12-28
Hi there,

Just as you don't *need* a swap partition, you don't need a /boot one either ... the advantages of each are slowly eroding, over time. Having said that, a dedicated /boot still has some advantages:

[LIST]
[*]You can put it anywhere you want, regardless of where the rest of your system might be.
[*]You can leave it dismounted after booting, so there's almost no chance of accidentally damaging it.
[*]If your system is very weird or very highly customised, you might need a /boot partition to make it work.
[/LIST]

Using a separate /boot partition doesn't make much difference to Grub's setup. You still have to cover all the same bases when it comes to things like making sure your partition numbering & kernel parameters are correct.

**Edit:** Almost nothing requires a reinstallation of a Linux system ... if you were (hypothetically!) interested in using a dedicated /boot partition, you could make the switch in 90 seconds. I just thought I should mention this, since your o/p said something about reinstalling.

---

### Post by IamAcoconut on 2007-01-14
> if you were (hypothetically!) interested in using a dedicated /boot partition, you could make the switch in 90 seconds. I just thought I should mention this, since your o/p said something about reinstalling.And how to make this switch?

---

### Post by Sef on 2007-01-14
If you are new to GNU/Linux, don't make a boot partition.  Keep things simple and as you learn more, you can decide if you want to make one or not.

---

### Post by bernied on 2007-01-14
I agree with Sef. That guide you linked to will work just as well without a separate /boot partition. In essence, you will have already mounted the /boot directory when you mount the / partition, because that is where it is located in your system. No compromise.

A separate /boot partition might become useful once you've installed your second or third linux distribution, if you are so inclined.

---

### Post by IamAcoconut on 2007-01-14
Ok, I hope this solves **ghepardo**'s problem, but it doesn't solve mine.
I need a boot partition, as I want to have others encrypted with LUKS. 
So how to 'switch' without damage to current system? 
Would following that guide do it?

---

### Post by kidders on 2007-01-14
Hi there,

To set up a dedicated /boot partition, you could do something like this:

[LIST=1]
[*]Create a new (small) ext2 filesystem. You can use something like **du -h /boot** to get a rough idea of *how* small.
[*]Mount the filesystem to, say, /mnt/newboot.
[*]Do a **sudo cp -dpR /boot /mnt/newboot**.
[*]Move /boot to one side, with **mv /boot /oldboot; mkdir /boot**.
[*]Tweak /etc/fstab to have /boot mounted read-only ... or not at all.
[*]Check your bootloader configuration to make sure that everything that should point to /boot still does, and that your kernel parameters point to / (rather than the /boot partition).
[*]Reinstall your bootloader, to be safe.
[*]Reboot.
[/LIST]

Now, any time you want to write to /boot, do a **sudo mount -o remount,rw /boot** first, to remove the read-only flag, or just a **sudo mount /boot**, depending on how /etc/fstab treats it.

Something along those lines should do the trick for you. :-)

---

### Post by IamAcoconut on 2007-01-14
Hey, thanks for quick response :)
Just last question - how do I reinstall bootloader?

---

### Post by bernied on 2007-01-14
That link in the first post tells you how.

---

