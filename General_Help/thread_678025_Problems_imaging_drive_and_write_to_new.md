---
title: "Problems imaging drive and write to new?"
date: 2008-01-25
forum: General Help
---

### Post by pepsi_max2k on 2008-01-25
Hey, I want to move the contents of a drive with Ubuntu / grub on it to a new, larger drive. Would I be ok just to do a straight image from the first and write it to the second? And at which point would I start getting grub or other errors? Resizing root partition? Resizing other partitions? Thanks.

---

### Post by jeffus_il on 2008-01-25
You can do a straight copy of the partition, afterwards you need to run grub-install to update the grub boot sector to access the new boot partition. There is a tool called suoergrubdisk which can do this for you automatically.

---

### Post by pepsi_max2k on 2008-01-25
>> afterwards you need to run grub-install to update the grub boot sector to access the new boot partition

so even after a straight out clone i'd still have to run grub-install? oh well... can i use the install disc to boot in to the OS first then? or can i run grub from the live install disk? or just supergrubdisk as you said? thanks for the help :)

---

### Post by jeffus_il on 2008-01-25
Yes, grub sits in a boot sector, not in the partition itself.

---

### Post by rosegarden78 on 2008-01-25
If you can spare the OS on your former drive,  why don't you back up your /home folder?  Then fresh install Ubuntu GG 7.10 with Vista/X like [this]("http://ubuntuforums.org/showthread.php?t=385981") and use an Xfce session for a cleaner look on your new, larger drive.

---

### Post by Irony on 2008-01-25
Simply copy Ubuntu to the new drive;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

If you have to change where grub points do;

```
sudo grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit
```

Which, in this example, would install grub to the MBR and point it to the grub/menu.lst in hda3.

---

### Post by pepsi_max2k on 2008-01-28
blimey well, i did a disk clone with Acronis True Image 8, and it's just booted up with grub fine without having to do anything else.

maybe it's the way i'd installed grub previously (grub-install /dev/hda using the grub-gfxboot package) or maybe i'm just lucky :popcorn: thanks all.

---

### Post by mtbsoft on 2008-01-30
> **Irony said:**
> Simply copy Ubuntu to the new drive;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

I have a Dell laptop which has the ATI graphic so it is a real pain to setup (especially if I stuff it up experimenting) so I want to use a spare bootable partition to experiment in.

I followed your post above to copy my existing install to the spare partition, hand modified my grub setting and fired up the new partition... but it didn't work, it stopped part way through "Waiting for the root file system" if I remember correctly.

I have /home in a separate partition and did nothing with it, I intended to reset the experiment partition to use one within the experimental partition to separate them.

I'm guessing that the fstab may not match up with the new partition but can't be sure how to fix it up.  You can see where I'm trying to get to, can you suggest how best to do this please.

---

### Post by phidia on 2008-01-30
> **mtbsoft said:**
> I have a Dell laptop which has the ATI graphic so it is a real pain to setup (especially if I stuff it up experimenting) so I want to use a spare bootable partition to experiment in.

I followed your post above to copy my existing install to the spare partition, hand modified my grub setting and fired up the new partition... but it didn't work, it stopped part way through "Waiting for the root file system" if I remember correctly.

I have /home in a separate partition and did nothing with it, I intended to reset the experiment partition to use one within the experimental partition to separate them.

I'm guessing that the fstab may not match up with the new partition but can't be sure how to fix it up.  You can see where I'm trying to get to, can you suggest how best to do this please.

Take a good look at /boot/grub/menu.lst and /or post that and your /etc/fstab 
You might also try the rescue broken system option that's on the alternate cd.

I'm running my laptop with gutsy from a usb drive and will be wanting to copy the system over to the internal soon. So I may be facing this issue too.

---

