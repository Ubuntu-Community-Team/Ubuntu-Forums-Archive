---
title: "Help On Installing A Second Copy Of Ubuntu On The Same Disk"
date: 2007-06-01
forum: General Help
---

### Post by boom2k1 on 2007-06-01
*I am not a Ubuntu guru.

I am now using Ubuntu 5.04 on a 4.8GB disk partition. The reason I want to install a fresh copy of Ubuntu is because 1. disk space and 2. quite a few things screwed up. However, it is still very usable and I have invested huge amount of time just getting every hardware to work (ie. having some scripts to gett the unsupported SiS laptop) video card to be able to display 1680x1050 on my external monitor while the laptop screen is off.).

Anyways, that means I won't want to screw up this copy of ubuntu unless I can replicate everything on a freshly installed Ubuntu 7.04.

My partitions are as follows:
/dev/hda10 /documents vfat 2.0GB
/dev/hda2 /windows ntfs 18.6GB
/dev/hda5 /storage ext3 9.6GB
/dev/hda7 ext3 / 4.8GB
/dev/hda8 ext3 /home 1.4GB

Would it be possible for me to install 7.04 on hda5?  (i can transfer everything in /storage to an external disk)?
How would I do that?

Below are some of my concerns:
1. would I be destroying the boot loader that let me choose which OS to run when the computer starts? (and also how could I modify that screen?)
2. would i be able to install another copy of ubuntu on that 9.6gb?
3. could i also use /home to share those customized settings? (what is /home anyways?)

Thanks.

---

### Post by reckless2k2 on 2007-06-01
The "new" bootloader will detect any other operating system on the disc and enable you to boot to them while showing which partition you are booting from as well.

ubuntu will more than fit on the 9.6BG partition. you just have to tell it to be "/" on install in the partitioner.

you can specify the /home partition you already have as your home partition again in the partitioner. just make sure not to format it at ALL.

---

### Post by Wim Sturkenboom on 2007-06-01
I would initially NOT share the home directory. Reason being that some config files might not be compatible which might give you some problems in either the one or the other version of Ubuntu or in both.

---

### Post by boom2k1 on 2007-06-01
thanks for your wisdom

---

