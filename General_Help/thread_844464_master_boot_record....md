---
title: "master boot record..."
date: 2008-06-29
forum: General Help
---

### Post by Dirty l3um on 2008-06-29
i seem to have royal skrewed up my master boot record.

Okay this is the story.

I was running windows XP on a 250 gb drive that i already had partitioned into a 150 and a 100.
-the 150 was named E:
-the 100 was named C:

E drive had my operating system on it while C was for my backing up of files.  I downloaded the ubuntu.iso and used power iso to mount it as an image.  i then proceeded to load it "as an application" in my windows C: partition.  the ubuntu.iso was saved on the c: and other than that it (the c:/ ) was empty.  since ubuntu was running as the mounted image i got into ubuntu and i re partition the c: into some seperate drives, 2 of them ex3 and a fat32.  I obvisouly made a huge blunder.  i deleted the iso image and NOW when my computer goes to restart it wont even recognize windows xp on my hard drive. (i didnt delete any files on the E:, only the c:/)  Im not sure if that was because of grub not seeing ubuntu and not knowing what to do, or what.  So at this point i found my old hard drive with xp on it, just incase i ever do something stupid like this.  so i booted off of that drive, re downloaded the .iso did it all over again and didnt skrew it up this time.  so i successfully have ubuntu running(thats what im using atm). the problem is, i can see all of the filesystems of my origional xp set up but i cannot boot off the origional xp drive.  another problem im having is the fact that i cannot boot up at all without my backup xp hard drive plugged into the ide connection. 

im guessing i deleted the MBR on the old drive and i have googled it to try to find some answeres, but i cant even figure out which drives are which...

so my question is how do i fix this so i can boot off my old system?

how do i figure out which drive is which and rewrite the MBR on that drive?

---

### Post by logos34 on 2008-06-29
If you have an XP install CD, boot into the REcovery console and run fixboot and fixmbr.  unplug the backup drive beforehand.  

Or dl the Super Grub Disk.

---

### Post by mempman on 2008-06-29
> **Dirty l3um said:**
> i seem to have royal skrewed up my master boot record.

Okay this is the story.

I was running windows XP on a 250 gb drive that i already had partitioned into a 150 and a 100.
-the 150 was named E:
-the 100 was named C:

E drive had my operating system on it while C was for my backing up of files.  I downloaded the ubuntu.iso and used power iso to mount it as an image.  i then proceeded to load it "as an application" in my windows C: partition.  the ubuntu.iso was saved on the c: and other than that it (the c:/ ) was empty.  since ubuntu was running as the mounted image i got into ubuntu and i re partition the c: into some seperate drives, 2 of them ex3 and a fat32.  I obvisouly made a huge blunder.  i deleted the iso image and NOW when my computer goes to restart it wont even recognize windows xp on my hard drive. (i didnt delete any files on the E:, only the c:/)  Im not sure if that was because of grub not seeing ubuntu and not knowing what to do, or what.  So at this point i found my old hard drive with xp on it, just incase i ever do something stupid like this.  so i booted off of that drive, re downloaded the .iso did it all over again and didnt skrew it up this time.  so i successfully have ubuntu running(thats what im using atm). the problem is, i can see all of the filesystems of my origional xp set up but i cannot boot off the origional xp drive.  another problem im having is the fact that i cannot boot up at all without my backup xp hard drive plugged into the ide connection. 

im guessing i deleted the MBR on the old drive and i have googled it to try to find some answeres, but i cant even figure out which drives are which...

so my question is how do i fix this so i can boot off my old system?

how do i figure out which drive is which and rewrite the MBR on that drive?

what u need to do is boot off an xp disc and go into recovery mode and type "fixmbr" and "fixboot"...these 2 commands will install ntldr (windows bootloader) on your master boot record and this will allow you to boot into windowsxp.

However, ntldr will not allow you to boot into ubuntu, so after you fix up your windows partition, using the method above, you'll need to boot off your ubuntu cd,go into console, and the do "grub" to go then select issue the setup command, this will install grub on your mbr, and with grub you'll be able to boot windowsxp or linux.

---

