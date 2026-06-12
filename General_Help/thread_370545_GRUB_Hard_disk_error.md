---
title: "GRUB Hard disk error"
date: 2007-02-25
forum: General Help
---

### Post by tomzx on 2007-02-25
Things have gone worst and worst. I cannot even load any operating system.

I have tried the ultimate boot cd without any success. Once I try booting from my hard drive I get

GRUB Hard disk error

and it freeze there. I can't do anything there. I also tried the super grub disk but it looks like crap that just doesn't do anything, pretty much like the ultimate boot disk.

I've tried using testdisk to repair my partition list but let say it didn't go much further. I have no idea where to go now (what to do).

---

### Post by rsambuca on 2007-02-25
A few questions...

Was your system ever booting properly?  If so, what were you doing prior to it not booting?  If no, what were you trying to install?

What are your system specs?  

What is this ultimate cd you are talking about?

---

### Post by tomzx on 2007-02-25
> **rsambuca said:**
> A few questions...

Was your system ever booting properly?  If so, what were you doing prior to it not booting?  If no, what were you trying to install?
It was booting properly. I played a bit with the /boot/grub/menu.lst and from then it started not going well.
> **rsambuca said:**
> What are your system specs?
AMD 64+ 3000+,
512 MB of ram DDR
400 GB hd (seagate)
128 MB Ati Radeon 9550
> **rsambuca said:**
> What is this ultimate cd you are talking about?
[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

---

### Post by rsambuca on 2007-02-25
Ahhh.  Starting to make sense now.  I suppose you didn't make a backup copy of your menu.lst?

Can you please post your /boot/grub/menu.lst and also list any changes that you made if you can remember.

---

### Post by tomzx on 2007-02-26
how can I post my /boot/grub/menu.lst? I cannot log in any OS and if I try loading GRUB again using the rescue broken disk from the live disk, it says I cannot install it on both partition.

What I've tried to fix is the partition table. I've used testdisk in order to recover my hd0,0 partition table which was overwritten when I installed GRUB. When I was in testdisk, I could see that my hd0,0 was corrupted since it could not list the files contained within. So I processed the drive and then saved the partition table. From then, I believe that when I started my computer, it would show up the GRUB Hard Disk Error.

---

### Post by rsambuca on 2007-02-26
Ok, I am confused because you never give us all of the information to fix your system.  So let's start at the beginning.

1.  What did you have on your system before you installed ubuntu?
2.  How was your harddrive partitioned prior to installation?
3.  When you installed ubuntu, did you manually partition the drive or use the automatic partition?
4.  You say it was booting fine until you started to make changes:  What changes did you attempt, and why were you trying to "fix the partition table"
5. When you attempt to boot now it gives you a grub error.  Could you please post exactly what it says?

---

### Post by tomzx on 2007-02-26
1. Win XP, Ubuntu, Vista
2. 1 Part containing Win XP (C:), 1 Part containing files (D:), Unbuntu + Swap (2 parts), Vista (G:)
3. I had already partitionned.
4. I was trying to get GRUB to allow me to boot into Win XP.
5. GRUB Hard Disk Error.

I used testdisk once more today, was able to recover some parts except my D: which for some reason was over all the parts after it so I got it deleted (the partition table I imagine).

I'm now into Ubuntu but like I mentionned in 5. that's what I get if I go to the Vista bootloader (which is in the boot list at the beginning).

---

### Post by rsambuca on 2007-02-26
What order did you install the OS's?

---

### Post by tomzx on 2007-02-26
Same as listed in 1.

1. Win XP, Ubuntu, Vista

But I had to reinstall Ubuntu since I couldn't go anywhere with the GRUB Hard disk error. I've come to realise there's a problem with my partition and I'm currently working on that...

---

### Post by tomzx on 2007-02-28
I've been able to check what was on my drive and noticed that the $BOOT file on my C: drive (the one where windows XP should boot) contains the "Hard disk error" (in hex format). So I suppose I'd have to edit my $BOOT in order to get the booting process to work correctly again, but I have no idea how I can do that. If anyone has an idea, I'd like to hear it!

---

