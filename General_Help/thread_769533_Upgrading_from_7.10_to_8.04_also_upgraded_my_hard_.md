---
title: "Upgrading from 7.10 to 8.04 also upgraded my hard drives from IDE to SATA !"
date: 2008-04-26
forum: General Help
---

### Post by linuxvacuum on 2008-04-26
Seriously, when I had 7.10 installed, my hard drives were know as hda, hdc and sda.

Now upgrading did the following :
hda -> sda
hdc -> sdb
sda -> sdc

So now when I fdisk -l, I get information for sda, sdb, sdc which are 3 sata drives that I don't have... Anyone care to explain that weird "conversion" ?

Good thing I am now more knowledgeable because after the upgrade, I was sent to a root prompt. I had to edit /etc/fstab...

---

### Post by skymera on 2008-04-26
hda is for ATA/IDE drives.
Sda is for **s**ata drives.

It's normal, my SATA are sda and sdb
My IDE drive is hda :)

---

### Post by TransitMan on 2008-04-26
I think you missed the point in the OP's question.

Why would IDE drives under 7.10, classified as hda, hdb, hdc suddenly be refered to as sda, sdb, sdc under 8.04 when the OP does not have and SATA drives installed, only IDE?

Could be something in the /fstab when the OS was installing. Otherwise, I really don't know.

---

### Post by Miljet on 2008-04-26
I'm running 7.10 on an old HP computer that only has one IDE drive. It has always shown up as sda. It hasn't caused any problems so I haven't spent too much time worrying about it.

---

### Post by LaRoza on 2008-04-26
That is the kernel's way of identifying drives. It is normal now.

---

### Post by linuxvacuum on 2008-04-26
So now every drive gets a sdx name? The distinction between IDE and SATA on drives numbering is gone? Do you please have a link explaining the change? I would like to know why, thanks.

---

### Post by BluntBox on 2008-04-26
I wouldn't mind reading about this too. Hardy refuses to mount a drive of mine, despite it being 100% operational in Gutsy, WinXp, Vista. So any info on changes etc would be great.

---

### Post by Skipster on 2008-04-26
> **linuxvacuum said:**
> So now every drive gets a sdx name? The distinction between IDE and SATA on drives numbering is gone? Do you please have a link explaining the change? I would like to know why, thanks.

as of the 2.6.21 kernel ide drives are using the same libata as sata so the drives are identifed as sdxx instead of hdxx.  it was a kernel decision and upstream from ubuntu.  pick any distro and you find that all are the same.  assuming they are using a current kernel.

---

### Post by electrofreak on 2008-05-10
> **LaRoza said:**
> That is the kernel's way of identifying drives. It is normal now.

I don't consider this normal.... IDE is NOT EQUAL to SATA.

In 7.10, I was running kernel 2.6.22.[something], then yesterday I upgraded to 8.04 and ran into this issue with 2.6.24.[whatever]. I've heard many different kernel revisions to blame for this, but all the them are less than the 2.6.22 kernel I was using before.... yet suddenly now my IDE HDs are /dev/sdXX. Why??????

It seems no one knows crap about why it is this way. It doesn't even make logical sense to change the naming of IDE HDs to sdXX.

But one thing that is apparent.... it's more than just a name change. It is also a functionality change because hdparm doesn't completely work anymore.

Believe it or not.... IDE Hard drives are still in use!!! If anything.... all hard drives (SATA and IDE) should just be changed to /dev/hdXX for the simplified identification of everything as a Hard Drive. Then things like flash drives could be /dev/usbdXX or whatever. And actual SCSI drives can be /dev/sdXX.

Who made these senseless naming decisions?? We need a better/updated naming convention/standard for /dev/.

But more than anything... we need the IDE drives to actually function as IDE HDs and SATA to function as SATA drives.

---

### Post by ghost_ryder35 on 2008-05-10
[http://lwn.net/Articles/194866/](http://lwn.net/Articles/194866/)
 
[http://www.gentoo.org/doc/en/kernel-config.xml](http://www.gentoo.org/doc/en/kernel-config.xml)
look for #3 on this link

---

### Post by Gina on 2008-05-10
I presume this made things easier for the kernel developers - unfortunately it's very confusing for the average user!

PS. I found the above explanation rather confusing.

---

