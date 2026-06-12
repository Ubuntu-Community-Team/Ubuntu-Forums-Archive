---
title: "Ubuntu to recover files from portable external hard drive (Mac Formated)."
date: 2013-06-25
forum: General Help
---

### Post by jfth24 on 2013-06-25
I'm to ask for help because Ubuntu is the only OS giving me hope for a possible solution right now.

Story short : I have an portable external hard drive (Western Digital), using it with a mac, probably formated in Mac OS extended. I accidentally deconnected the external HD while Mac OS was duplicating a file on it. Now the disk wont mount anymore. It looks dead.

- Cant mount the HD on my Macbookpro
- Disk utility cant see it
- The hard drive wont show on terminal commands
- Disk Warriors (Wich is said to be the ultimate tool for hard drive repair/data recovery) wont see it either.

I knew Linux was more powerfull than windows and Mac OS so I booted with live CD, the portable hard drive still cant be mounted but if I launch Gparted I can see my external hard drive on the list! (Yeah! there is hope). Problem is Gparted see no partitions and no file system.

[ATTACH=CONFIG]244148[/ATTACH]

I didnt take any actions yet as I want to make the best move to recover my files and folder structure from this drive. The disk contain PSD, jpegs, ai (illustrators), eps, lots of footage from 5D MarkII, Mp3.

I did read about Photorec being able to recover the files on another hard drive but It doesnt keep the folder structure (does it?) :(
I did read about Testdisk but I'm not sure it's safe to try to repair the disk partition I feel nothing should change on the damaged disk right now...
Knoppix Live CD is said to be the best thing. I did try it but I'm totally lost. I feel ubuntu would be powerfull enough to recover the files.
and I know nothing about terminal commands, I can copy paste them but I dont know the language at all.

I need help and tips about what is the next step I should take. What sofware to use.

Thanks again!

---

### Post by dino99 on 2013-06-25
Sorry i dont know about Mac commands; but if that hdd was working, then it simply mean it is into a bad state. Linux have "fsck" to force a partition checking, and repair the found errors; i suppose you can also do something similar with Mac (with unmounted partition)
[http://linux.aldeby.org/post/linux-ubuntu-force-fsck-filesystem-check-at-reboot.html](http://linux.aldeby.org/post/linux-ubuntu-force-fsck-filesystem-check-at-reboot.html)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by jfth24 on 2013-06-25
My intentions is to repair or recover the files from Ubuntu. My Mac cant see the disk at all so I wont use Osx for this.
Ubuntu seem more powerfull.

I guess this would be doable from the live CD but I dont know what steps I should take.

---

### Post by dino99 on 2013-06-25
> **jfth24 said:**
> My intentions is to repair or recover the files from Ubuntu. My Mac cant see the disk at all so I wont use Osx for this.
Ubuntu seem more powerfull.

I guess this would be doable from the live CD but I dont know what steps I should take.

i understand, but:
- its better and more secure to repair with the original tool
- if you take the gparted route, then check that it can recognize the mac partition (note which kind of format is used). Its possible that the partition(s) is/are well, but only the partition table is borked. Gparted is able to rebuild that table without damage for the partition/data, so try that first. An other solution is to try duplicating the mac partition before trying to repair that issue (gparted can do that too)

[http://www.sudo-juice.com/how-to-clone-a-hard-drive-in-ubuntu-linux/](http://www.sudo-juice.com/how-to-clone-a-hard-drive-in-ubuntu-linux/)

---

### Post by btindie on 2013-06-25
Paste the output of
```
sudo parted /dev/sdc print
```
but looking at gparted, I don't hold much hope for you. It looks like all the partitions may have been deleted.

You may also want to give gpart a go though I'm not sure if it supports MacOS formatted disks
```
sudo apt-get install gpart
sudo gpart /dev/sdc
```

---

### Post by jfth24 on 2013-06-25
Thanks for the tips I will try.
Most of the files should be on the disk. I disconnected my hard drive when it was duplicating a 40k file on it.
The partition table must be damaged but the files are ok I'm sure... Well almost sure.

---

