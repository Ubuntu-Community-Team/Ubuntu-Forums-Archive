---
title: "Ubuntu 7.10 Uninstallation help"
date: 2008-04-08
forum: General Help
---

### Post by Blaker1 on 2008-04-08
Hello, I am wanting to remove Ubuntu from my F: drive and just load Windows XP like I used to. I used the wubi-installer that came in the ISO of Ubuntu 7.10. Yes I know, "just go to add/remove programs and uninstall wubi" or "go to C:/wubi/uninstaller.exe".... Neither of these are there though? there is no Wubi folder at all and I also can't see my F: and G: (G is partioned from F: ) drive now that Ubuntu is on F:.

Please help.

Oh and here is a screenshot of my 'Computer Management': [http://blaker101.elementfx.com/dump/CMs-01.png](http://blaker101.elementfx.com/dump/CMs-01.png)

---

### Post by kpkeerthi on 2008-04-08
[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by njparton on 2008-04-08
Use the windows disk manager to delete your F: partition and then use easybcd to remove the wubi entry in your windows boot file. If there's anything in add/remove programs related to wubi or ubuntu, uninstall that first.
 
**Edit***
just realised you're using XP not Vista.  You'll need to use something other than easybcd to edit your windows boot config.

---

### Post by Blaker1 on 2008-04-08
What about GRUB?

And if I deleted my F: partion, would all the space go to C: ?

---

### Post by Blaker1 on 2008-04-08
BUMP! Could I simply use the Computer Management to delete the partion (and the space will go bakc to C: ... right?) then restart the pc and boot the recovery console and do a "FIXMBR" ? because GRUB wont work when I remove the partion so shouldn't FIXMBR fix it.

---

### Post by njparton on 2008-04-09
If you delete the partition you could then extend your C drive space into the free space so long as they're next to each other on the hard drive.
 
Yes, you'll probably have to use the XP CD to fix you're MBR if you want to remove grub, but there are loads of guides out there specifically on how to do that. Search for them first.  The partitioning is the easy bit here, your MBR is the hard bit.

---

### Post by Blaker1 on 2008-04-09
Thanks.

I downlaoded PartitionMagic 8.0 and anything I attempt to do works, then click the "apply" button and everything goers back to what it was? is this a bug or is it me?

Oh and the MBR should be the easy bit; Reboot pc, press ESC, choose to boot from XP cd, and get to the recovery console (been there before :) ).

---

### Post by njparton on 2008-04-10
Partitionmagic is a great program, but for simple things doesn't offer anything that the unbuilt disk manager (under administration options in control panel) can.
 
Use the latter and see if it works.

---

### Post by Blaker1 on 2008-04-10
Nevermind, I ahd a trial of it :p i got a 'legal' full version from a forum and I now its all good, Im back to just booting with windows and i have my drive back.

Thanks for all the help you guys have given me ;)

---

### Post by harrybazeegar on 2008-04-10
if ever you delete your linux partitions and then your computer does not boot...
1. insert your windows CD
2. log into recovery mode console
3. log in as administrator (if you have to)
4. fix the MBR
5. voila!

---

