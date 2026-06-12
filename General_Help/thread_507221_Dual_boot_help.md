---
title: "Dual boot help"
date: 2007-07-22
forum: General Help
---

### Post by tallguy240 on 2007-07-22
I currently have a dual boot system that is running XP Pro and Ubuntu 7.04 with Grub as the bootloader.  I would like to remove windows, resize the partition and reinstall windows onto a smaller partition and dedicate the recovered space to my ubuntu OS. I have found numerous articles on setting up a dual boot system but not removing, resizing and reinstalling. Can anyone lend any assistance whether it be links or 'How To's' etc... I only need limited space now for the evil OS. Thanks.

---

### Post by brent113 on 2007-07-22
This is an easy one: boot from the live cd and open GParted (System->Administration)

Use that to find the partition your windows install is on (it will be NTFS) and delete it.  Then resize your linux partition.  Then create a new partition, smaller for your windows install.  You don't have to format it since Windows will do this as part of its install.

Beware, Windows will overwrite grub and pretend linux doesn't exist.  So after windows is installed, you will have to boot back from the Ubuntu live CD and install grub again, you can follow this: [http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

Either the first or second posts work, just different methods.

---

### Post by tallguy240 on 2007-07-23
Thanks. I will give this a go. I appreciate the help.  I have been using computers for a lot of years but this is one of those things I just have never done yet. Always just started over or went back to windows. Thanks again.

---

