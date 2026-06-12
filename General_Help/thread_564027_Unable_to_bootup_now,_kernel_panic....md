---
title: "Unable to bootup now, kernel panic..."
date: 2007-09-30
forum: General Help
---

### Post by Izobalax on 2007-09-30
Evening all!

I'm currently communicating with thee via the use of a Freespire 2.0 Live CD. The reason I am doing this is because my computer won't boot up into Linux anymore.

Yesterday, I booted up and before I got to my Ubuntu splash (where it loads up the kernel and stuff), the screen went blank and my Caps Lock and Scroll Lock keys were flashing. Not good. So I restarted the machine went into recovery mode and the booting up process (in text mode) told me that it couldn't mount the main hard drive because there was an unknown block and this caused a kernel panic. So, I restarted the machine again, entered the GRUB menu and booted up in kernel 2.6.20.15, instead of my standard 2.6.20.16. Yesterday, that worked fine.

Today, BOTH kernel versions won't boot up, the recovery mode text bootup given me the same problem, causing a kernel panic.

Today I've been trying to run the Freespire 2.0 Live CD and attempting to back up my personal data onto DVD-RW's, without success.

I tried taking the main HDD from my girlfriend's computer, sticking it in mine and trying to transfer the data from my HDD to my girlfriend's. Unfortunately, the Freespire 2.0 Live CD can't read my girlfriend's HDD.

So... I need help. Does anyone know how I can resolve this kernel problem? PWEESE????

---

### Post by cmnorton on 2007-09-30
Someone else will have a more knowledgable answer than this, but here goes:

Assuming you did not install something that caused this, boot from a live CD, and run fsck, assuming your boot partition is ext2 or ext3. If you have not installed anything wierd or did not drop the computer, then your boot problem might be a bad disk.

If your bios can be configured to boot slower and check all the memory, I'd suggest doing that.

---

### Post by Izobalax on 2007-09-30
> **cmnorton said:**
> Someone else will have a more knowledgable answer than this, but here goes:

Assuming you did not install something that caused this, boot from a live CD, and run fsck, assuming your boot partition is ext2 or ext3. If you have not installed anything wierd or did not drop the computer, then your boot problem might be a bad disk.

If your bios can be configured to boot slower and check all the memory, I'd suggest doing that.


OK, I'm still pretty much a n00b to these things. Talk me through, step by step. 

I'm using the Freespire Live CD now. How do I run fsck on my HDD? I doubt it is a HDD problem, but I can always try. 

Also, how would I configure my BIOS to boot slower?

/izo

---

### Post by Izobalax on 2007-10-01
OK, I've now booted up into my Ubuntu Feisty Fawn Live CD (*I've found it now*). However, in order to burn my personal data from my HDD to some DVD's, I need root access to my HDD. 

I don't know how to get root access to my HDD. 

HALP?

/izo

---

### Post by Izobalax on 2007-10-02
Since I can't fix my computer, I need to backup my personal data from my HDD. 

How can I do this when running my system from a Live CD? Please *help!*

/izo

---

### Post by Izobalax on 2007-10-02
Well, reading around here, I've figured that I can open two Nautilus windows in root using:

```
gksu nautilus
```

From here, I can access my HDD in one window and copy over the files to the other root window where I can use the CD/DVD Burner. 

Problem now is, it starts working but then *freezes* soon after it starts burning. 

PLEASE HELP!

/izo

---

### Post by tgalati4 on 2007-10-02
I'm assuming this is a desktop computer.  It sounds like a failing disk drive.  It works for a while then heats up and stops working.

Try opening the case, cleaning out the dust and physically moving the drive to allow more air circulation.

You are doing the right things, but you need to keep the drive working long enough to capture the data. 

Rather than burning CD's, get some 2 GB USB flash sticks and use those, then move the files to another machine for burning.  You need to copy the files quickly, and burning a CD takes a long time--long enough for the drive to lock up.

The fact that your old kernel worked then stopped working to me indicates that your drive is working long enough to boot, but not much after that.  You need to keep the drive cool to allow it to work longer. 

You only have one shot to grab your data, so plan carefully.  Don't reboot too many times otherwise the drive will fail completely.

---

