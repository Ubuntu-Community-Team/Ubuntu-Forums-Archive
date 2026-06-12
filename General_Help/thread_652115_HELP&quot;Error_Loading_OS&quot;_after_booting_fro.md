---
title: "HELP:&quot;Error Loading OS&quot; after booting from Live 7.10 CD"
date: 2007-12-28
forum: General Help
---

### Post by fth on 2007-12-28
I booted my machine with Live CD, did not install or anything. It booted fine. I then restarted my machine, without the CD, assuming XP would boot as it always used to, since I did not install anything. All I get is "Error Loading OS" and the cursor keeps blinking.
I have 3 HDDs on this machine and the one with XP has 3 partitions (total 5 partitions in 3 hdds). The partition XP was installed on used to be my "C:" drive, after Live boot, it reads "E:"
Now, I tried the recovery console and from what I can tell from DiskPart, my boot.ini points to the correct drive and partition.
I am not sure what Ubuntu Live CD might have changed but I was under the impression that the purpose of having a Live CD was to not change anything on the machine.
I am guessing the MBR is messed up but I am afraid to touch it since the drive has a ton of stuff I don't want to lose.
Please HELP.............

---

### Post by overdrank on 2007-12-28
> **fth said:**
> I booted my machine with Live CD, did not install or anything. It booted fine. I then restarted my machine, without the CD, assuming XP would boot as it always used to, since I did not install anything. All I get is "Error Loading OS" and the cursor keeps blinking.
I have 3 HDDs on this machine and the one with XP has 3 partitions (total 5 partitions in 3 hdds). The partition XP was installed on used to be my "C:" drive, after Live boot, it reads "E:"
Now, I tried the recovery console and from what I can tell from DiskPart, my boot.ini points to the correct drive and partition.
I am not sure what Ubuntu Live CD might have changed but I was under the impression that the purpose of having a Live CD was to not change anything on the machine.
I am guessing the MBR is messed up but I am afraid to touch it since the drive has a ton of stuff I don't want to lose.
Please HELP.............

Hi and did you have to change the boot order to be able to boot the cd?

---

### Post by fth on 2007-12-28
I changed the boot order from the Bios to boot first from CD and reverted back to HDD once I was done with the CD. Tried fixmbr, fixboot, etc. as well from the XP recovery console. Still get the same error.

---

### Post by mik1250 on 2007-12-28
So am I. I have nearly the same configuration and wanted to try ubuntu with the downloaded iso-image. So I´ve got the same error and tried also fixmbr, fixboot without success. Any help? Thanks a lot.

---

### Post by overdrank on 2007-12-28
> **mik1250 said:**
> So am I. I have nearly the same configuration and wanted to try ubuntu with the downloaded iso-image. So I´ve got the same error and tried also fixmbr, fixboot without success. Any help? Thanks a lot.

Ok Hi and welcome to the both of you, I have installed ubuntu several times with windows and have never had this happen. I am at a lost to help at the moment and I will search and think on what could resolve this issue. I do believe that the live cd does not rewrite or modify the mbr unless it is installed and the grub also. :(

---

### Post by zerof on 2007-12-28
Im having the exact same problem as you guys. I searched google for a solution and came across this forum. I  realized that I had burned a copy of ubuntu so that I can install it on my computer. I just had it boot up but nerver installed it just like some of you guys did. The next day I try to boot up and bam my OS wont load. I was able to fix my problem by simply putting the burned copy of ubuntu in my drive and having it boot up. Once the cd booted up and the boot options were displayed, I selected the last option which is boot from Hard Disk...or something like that. This worked for me and hopefully it will work for you guys. The last thing I needed was to lose all my stuff on my HD :) Good Luck.

---

### Post by fth on 2007-12-29
I finally fixed it.
Unplugged all other HDDs and it finally worked.
Hope this helps others in same situation.

---

