---
title: "clonezilla live CD won't boot with Lucid Lynx on G4 Mac"
date: 2013-05-19
forum: General Help
---

### Post by Celebes Kalossi on 2013-05-19
Downloaded and burned the iso for clonezilla live to a CD, since I wanted a backup of 10.04 before I go mucking around trying to set up a LAMP server. Data verified ok (I burned it on OS 10.8 if that matters) Thing is, I hold down "c" to boot to CD, the disc spins up but nothing happens and the screen goes back to the part where it says "press c to boot from cd" or if you just wait, it boots to ubuntu. I press "c" over and over but it keeps going back to that screen and I finally give up. Ubuntu boots just fine. This is a clean install that I just did on my old PowerPC G4 1.42 mac mini. Perhaps I need an older version of clonezilla to work with Lynx or the PPC machine? The standard searches yielded nothing. Thanks in advance!

---

### Post by sudodus on 2013-05-19
Are you sure that the downloaded Clonezilla iso file was made for powerpc?

Booting Clonezilla will be independent of what is installed in the computer hard disk drives.

---

### Post by Celebes Kalossi on 2013-05-19
I can't find a different iso for PPC and the site doesn't seem to indicate that there's a different iso. I don't even know if there is one, but the thought crossed my mind.

---

### Post by sudodus on 2013-05-19
Then I think you need some other tool to backup your Lucid system. (I checked after my reply, and couldn't find any powerpc version either.)

Is it important to have a complete backup image. In that case you can always use dd (run from an external drive, for example the Ubuntu install CD). dd is nicknamed 'disk destroyer', because it does what you tell it to do without questions. So if you tell it to wipe the system instead of backing it up ... So triple check that you get all the details right!

change directory to the partition on an external drive, where you want to backup
```
cd ...
sudo -s                                                 # start a superuser shell
dd if=/dev/sdx bs=4096 | gzip > dd-sdx.gz
exit                                                    # exit from the superuser shell
```

where x is the drive letter. Typically it is a for a single internal drive: if=/dev/sda

-o-

But you can also select some other kind of backup, for example a method based on ***rsync***. There are several backup tools available, that do not create images, and such methods work well with linux.

---

