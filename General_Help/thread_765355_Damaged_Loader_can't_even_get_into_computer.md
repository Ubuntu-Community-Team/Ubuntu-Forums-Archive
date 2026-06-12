---
title: "Damaged Loader can't even get into computer"
date: 2008-04-24
forum: General Help
---

### Post by rock122 on 2008-04-24
So I had Vista and Ubuntu 7.10 installed. As mentioned in another post my Ubuntu went through some problems and became unbootable. I decided to erase the ubuntu partition and re-install. At almost the very end of the install it gave an error that it couldn't read something from the disc due to it being dirty. The install then quit and now when I restart the computer I get this error

Grub Loading...
Error 15

So now I cannot even get into Vista! Worse even is when I go ahead and try to install ubuntu again it no longer finds any free space to install in and just wants to erase the whole hard disc. (The partitioner I use is in windows which I can't get into...)

Please help, I urgently need some of these files!

---

### Post by Mainiak Blaniak on 2008-04-24
Can you boot from a live CD?

MB

---

### Post by Steve1961 on 2008-04-24
> **rock122 said:**
> So I had Vista and Ubuntu 7.10 installed. As mentioned in another post my Ubuntu went through some problems and became unbootable. I decided to erase the ubuntu partition and re-install. At almost the very end of the install it gave an error that it couldn't read something from the disc due to it being dirty. The install then quit and now when I restart the computer I get this error

Grub Loading...
Error 15

So now I cannot even get into Vista! Worse even is when I go ahead and try to install ubuntu again it no longer finds any free space to install in and just wants to erase the whole hard disc. (The partitioner I use is in windows which I can't get into...)

Please help, I urgently need some of these files!

Repair with your vista DVD or if you haven't got a disk try the vista recovery disk from the makers of easyBCD:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by thelugnut on 2008-04-24
You might try this ..

1. Insert Windows CD into drive.
2. Boot into Recovery Console.
3. Type: fixmbr
4. Log into Windows
5. Navigate to Control Panel> Administrative Tools> Computer management> Disk Configuration.
6. Format the Ubuntu partition with ntfs.

Now this works for Windows XP. I don't have,(and will never have) Windows Vista, so I don't know if it is exactly the same or not. At least it should point you int he right direction.
Good luck !

---

