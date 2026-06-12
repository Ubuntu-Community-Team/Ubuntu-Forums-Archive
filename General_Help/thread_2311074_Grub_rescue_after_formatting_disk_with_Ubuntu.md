---
title: "Grub rescue after formatting disk with Ubuntu"
date: 2016-01-24
forum: General Help
---

### Post by andrey38 on 2016-01-24
Hallo!
I have a problem:
1. I installed Ubuntu + Grub + Windows 7 - each OS on separate hard disk.
2. Later I wanted to delete Ubuntu, but did it in wrong way - **formatted all parts of logical disks with Ubuntu **by PARAGON, and then create new partition as NTFS.
3. After reset computer - it shows:
error: no such device : fcfe1307-.....-......-.....
grub rescue >
4. **I can't enter to BIOS **for tuning load query for booting with LiveCD or whatever.

I've searched a long time for answer on the question - "what to do???" but nothing found.
Please help me return grub or bootloader to boot in to Windows....
THX

---

### Post by ajgreeny on 2016-01-24
Unfortunately the windows bootloader was removed from the hard disk when you installed ubuntu and now you have removed all the ubuntu partitions there are no longer any configuration files remaining for grub.

If you have an install DVD for Windows 7 you can run a repair of the bootloader to enable you to use windows again; if you have no DVD which is most likely your situation (as Microsoft generally did not ship them with new OEM machines but recommended you to make your own recovery DVDs) you will need to search for how to recover Windows 7 bootloader by other means.
See [http://ubuntuforums.org/showthread.php?t=1873884](http://ubuntuforums.org/showthread.php?t=1873884) for some suggestions.

I know the lilo suggestion of oldfred worked in WinXP but have never used Win 7 or anything newer than XP, but worth a try, I think.

---

### Post by andrey38 on 2016-01-24
The main problem was unable to enter into BIOS.
I've spent a lot of time to do anything. But couldn't manage it.
During googling i've found advice that help me!
"You would need to pull the system battery and CMOS battery if it doesn't  have a reset pinhole as otherwise the CMOS batt will keep the mainboard  from actually reseting."
So spent a lot of time to diassemble my laptop, remove CMOS battery, then assembly it.
After reboot,at last, it was able to enter BIOS.
Now I'll try to restore bootloader by Windows install DVD.

---

### Post by rigel4 on 2016-01-24
In Windows get to the system repair option>
Once there choose command prompt and change x:
to C: do a DIR to make sure you are in the system partition..

then type bootrec /fixmbr
then do bootrec /fixboot

reboot the system to windows :)

---

### Post by andrey38 on 2016-01-24
Solved!
I've already fix my problem... Ufff it was hardly...
But now I know every screw inside of my laptop)

---

### Post by ajgreeny on 2016-01-25
Wonderful, and well done!

Please mark the thread as SOLVED from the Thread Tools menu at the top.
I have now marked as solved on your behalf; it is helpful to those searching for answers to see threads with solutions.

---

