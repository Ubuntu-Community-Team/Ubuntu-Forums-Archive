---
title: "The right way to make a full system backup?"
date: 2008-02-20
forum: General Help
---

### Post by Kivech on 2008-02-20
Ok, here goes:

I have Ubuntu 7.10 x64 on my PC. It's all configured the way I want to now. I added quite some things to the original installation (screenlets, compiz plugings, cairo-clock, awn curves, etc.).
What I want to do is make a backup in such a fashion that if tomorrow my disks crash, I can put new ones in and restore my system exactly the way it is now, without having to do anything but restoring my system (if possible).

I have my /home directory on a seperate disk and my overall partitioning scheme looks like this:

/boot
/swap
/
/usr
/var
/tmp
/home (on a seperate disk)

Where /, /usr, /var and /tmp are on an extended partition.

Now what and how should I back up these partitions in order to be able to restore my full system without having to reinstall software, addons/addins, etc. Of course, as simple as possible.

Thanks in advance for any advice you guys can give me.

Kivech

---

### Post by Het Irv on 2008-02-20
See QuickStart in My sig. I think that is what you are looking for.  It will do a full backup in three parts, /, /home, and config files.  Store it on a seperate drive along with a copy of the program.  You can then run the program from the external and restore all of your data.

---

### Post by Kivech on 2008-02-20
Thanks Irv, I'll have a look at it. ;)

Kivech

---

### Post by UK-Wobbie on 2008-02-20
You can use this tool Remastersys!
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)
Top tool i love it :lolflag:
It will make a FULL System backup of your computer and make a ISO image what you can burn on to a DVD disk, Making a Live CD of your System :)
Then you can install your computer back anytime by using the disk, How it was with everything on it and back the way it was!

---

### Post by Kivech on 2008-02-20
> **UK-Wobbie said:**
> You can use this tool Remastersys!
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)
Top tool i love it :lolflag:
It will make a FULL System backup of your computer and make a ISO image what you can burn on to a DVD disk, Making a Live CD of your System :)
Then you can install your computer back anytime by using the disk, How it was with everything on it and back the way it was!

Looks very interesting, I might have a go with this one. Thanks mate!

---

