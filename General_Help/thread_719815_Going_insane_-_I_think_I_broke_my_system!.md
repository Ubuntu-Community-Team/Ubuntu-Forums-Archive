---
title: "Going insane - I think I broke my system!"
date: 2008-03-09
forum: General Help
---

### Post by sajro on 2008-03-09
I'm totally freaking out right now. I was resizing my partition via GParted on SystemRescueCD and I think I deleted everything on my Linux partition when I accidentally cancelled! Oh my gosh I need that stuff (I don't have an external backup!). My dad has all his students' things on there he needs.

How can I fix this? Grub gives me like error 2 or something. I'm on a Puppy livecd at the moment. I'm freaking out more than I can ever remember freaking out. Please help if you can!

---

### Post by sajro on 2008-03-09
I know bumping is bad etiquette; I'm sorry. I'm so worried!

---

### Post by KeyserSoze93 on 2008-03-09
Can you run Gparted from puppy? Does that show you disk usage? I asume you haven't had any luck mounting it while running the live distro... 
You can try and image it as well (dd if=you_dodgy_hdd of=image.img)

---

### Post by v1cho on 2008-03-09
If it's something with partition table or file system - try TestDisk ([http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)). Otherwise wait the geeks to respond :)

---

### Post by sajro on 2008-03-09
Think I should run GParted's 'check filesystem and (if possible) repair errors'?

---

### Post by walsh416 on 2008-03-09
Can you reboot and run a mem test?

---

### Post by sajro on 2008-03-09
> **walsh416 said:**
> Can you reboot and run a mem test?

I could if I knew how to do that even though  GRUB doesn't get to the boot menu where I could select "Ubuntu 7.10 memtest86" or w/e.

---

### Post by fillintheblanks on 2008-03-09
heh it was nice knowing you

---

### Post by sajro on 2008-03-09
> **fillintheblanks said:**
> heh it was nice knowing you

Thanks for your helpful suggestion...:rolleyes:

---

### Post by tgalati4 on 2008-03-09
Well, this is a tough one.

There are two things to do in a dire situation:

1)  **Situational Awareness**--What is working and what is not?  What resources do you have available?  Who else can help you?  It helps to sit down, take a deep breath and start writing these things out.  The forums are busy and help doesn't come instantly.

2)  **Triage**--There is a time factor involved.  You have to determine what things you can do right away and what things can wait.  I presume that you are trying to fix this computer before your father finds out.  That may not be the best strategy.  You want to preserve data--that is most important.  Don't ball up the machine further.

As far as helping you, I have no idea what kind of computer, what size hard disk, what was the orginal operating system.  So help will be slow in coming without specific details.

Is this a desktop computer or a laptop?  You said that you canceled out of paritioning "my" partition?  If so then the data on the other partitions should be OK.  Just because GRUB complains is no reason to get excited.  GRUB usually complains when you mess with partitions.

Boot puppy linux, and post the output of (from a terminal):

>df -h

I don't know if puppy automatically mounts all partitions that it sees.  Go to /mnt or /media and report what you see.

> cd /mnt

> ls -la

> cd /media

> ls -la

---

### Post by sajro on 2008-03-09
> **tgalati4 said:**
> 1)  **Situational Awareness**--What is working and what is not?  What resources do you have available?  Who else can help you?  It helps to sit down, take a deep breath and start writing these things out.  The forums are busy and help doesn't come instantly.

What works: RAM, CPU (obviously), swap partition (important, yes? means hd itself is okay?), net (obviously), monitor (obv.), kb/mouse. Don't know anyone more tech-savvy than I except people on forums (which is sad in retrospect considering I can't figure this out). 

> 2)  **Triage**--There is a time factor involved.  You have to determine what things you can do right away and what things can wait.  I presume that you are trying to fix this computer before your father finds out.  That may not be the best strategy.  You want to preserve data--that is most important.  Don't ball up the machine further.

Time isn't my worry; I'm sure my dad will be ok. I'm just worried about successfully getting as much stuff back as possible and hopefully having our system back.

> As far as helping you, I have no idea what kind of computer, what size hard disk, what was the orginal operating system.  So help will be slow in coming without specific details.

It is a Dell Dimension 2400. ~2.6GHZ Celeron (single core). 768MB of DDR2 RAM. ~80GB (like 79.8 or something) Seagate (I believe) HDD. Although it's likely unrelated, it's a Dell/Logitech wired kb/mosue and a Dell 15-inch LCD monitor.

The original OS was Windows XP, but we changed to exclusively Kubuntu a few months ago.

> Boot puppy linux, and post the output of (from a terminal):

>df -h
```
Filesystem                Size      Used Available Use% Mounted on
tmpfs                     1.3G     50.0M      1.3G   4% /initrd/pup_rw
tmpfs                   103.9M    103.0M    892.0k  99% /initrd/mnt/tmpfs
/dev/loop0              102.9M    102.9M         0 100% /initrd/pup_ro2
unionfs                   1.3G     50.0M      1.3G   4% /
shmfs                   159.5M         0    159.5M   0% /dev/shm
```

About the partitions...```
mount: can't find /dev/hda3 in /etc/fstab

```

Hope that gives you more info!

---

### Post by tgalati4 on 2008-03-09
I'm not familiar with the Dimension 2400.  I assume it's a standard desktop machine.

Post the output of:

>sudo fsck /dev/hda1

>sudo fsck /dev/hda2

>sudo fsck /dev/hda3

What partition is the swap file?  How large to remember it to be?

I'm going to a house warming party, so I'll be out for a few hours.  Good luck.  You are in quite capable hands.  If the worse happens, please leave an address for flowers.

---

### Post by sajro on 2008-03-09
> **tgalati4 said:**
> 

Post the output of:

>sudo fsck /dev/hda1

>sudo fsck /dev/hda2

>sudo fsck /dev/hda3

What partition is the swap file?  How large to remember it to be?

I'm going to a house warming party, so I'll be out for a few hours.  Good luck.  You are in quite capable hands.  If the worse happens, please leave an address for flowers.

Thanks for making me laugh. I really needed that after this freakout. Let's hope the negotiations with my HDD negate the need for flowers.
[B]
fsck /dev/hda1 (running as root already in Puppy):[/B]
```
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/sbin/e2fsck: No such device or address while trying to open /dev/hda1
Possibly non-existent or swap device?

```
Don't think I have a hda1 partition. Same for 2, but here goes...

**fsck /dev/hda2:**
```
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/sbin/e2fsck: No such device or address while trying to open /dev/hda2
Possibly non-existent or swap device?

```
I was right...here's three: the problem child...

**fsck /dev/hda3:**
```
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Group descriptors look bad... trying backup blocks...
/sbin/e2fsck: Filesystem has unexpected block size while trying to open /dev/hda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
Now, I'm pretty tech-savvy for the most part but this is a big WTF moment for me. I have no idea what that means.

The swap is hda4 and is 1.86GB (according to GParted).

Enjoy your party; I'm sure the many other experienced users can help!

---

### Post by Feivel on 2008-03-09
What happens if you boot with a Supergrub CD?

---

### Post by sajro on 2008-03-09
> **Feivel said:**
> What happens if you boot with a Supergrub CD?

Grub can't mount the partition to put itself in the /boot directory.

---

### Post by Feivel on 2008-03-09
> **sajro said:**
> Grub can't mount the partition to put itself in the /boot directory.

Well I'm out of ideas :)

---

### Post by perixx on 2008-03-09
I recommend this page, It's got great comprehensible GRUB information and a really really helpful troubleshooting section!:
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")
Most especially, refer to the > Ubuntu Booting problems


EDIT: you might want to save your current (faulty) bootsector with the 'dd' command (if there's any recognized partition?): > dd if=/dev/[SOURCE PARTITION] of=/[DESTINATION PARTITION]/bootsect.lnx bs=512 count=1 This will save the questionable bad partition's bootsector or MBR (e.g. of /hda1) to a file (/bootsect.lnx) on [DESTINATION PARTITION] (e.g. sda1), so you can still recover it and start over again, if you try to manually re-install GRUB again:
> sudo grub-install --root-directory=/media/[MOUNTED TARGET PARTITION] /dev/[MOUNTED TARGET PARTITION]
You may still need to edit your Grub's bootmenu /[MOUNTED TARGET PARTITION]/boot/grub/menu.lst accordingly. 

You'll have noticed, that you need to be able to mount the partition first, so you'll have get the filesystem working first (with e2fsck)... but once you are that far, this might be of help to you... prior to those measures, I recommend you to follow the suggestion of the poster above, and save the contents of your faulty partition to another, good one first (hope that works for you)...

Btw., you can try the UBCD (Ultimate Boot CD), to 'memtest' your PC (and also to tinker around with your MBR and bootsectors, once you've gathered enough information.

Good luck!


perixx

---

### Post by tgalati4 on 2008-03-09
I'm back from the party and you are still alive.  So that's good news.
So you know that swap is on /dev/hda4.  What is on /dev/hda1 and /dev/hda2?

So if /dev/hda3 is the bad actor, you need to recreate it's headers so that it does describe an ext2 or ext3 file system.  There are a couple of ways to do this.

One was suggested by fsck, that is, use a backup superblock to describe the file system.  This is usually safe.

>sudo fsck /dev/hda3 -b 8193

There are typically multiple copies of the superblock and fsck will try each one in order.

The other method is to use cfdisk and rewrite the partition, but this is riskier.

>sudo cfdisk /dev/hda

This will read all the partitions and simply rewrite the partition table.  Assuming that the sizes appear correct, will get you back to a recognizable ext2 or ext3 partition that puppy linux can mount and that you can browse the files.  Make sure the "b" or boot symbol is next to your hda3 partition.  Press "b" in cfdisk when the proper boot partition is highlighted.

cfdisk will warn you of possible loss of data, but that's a standard warning when rewriting the partition table.  I've rescued a few disks this way so it is a simple and effective method.

---

