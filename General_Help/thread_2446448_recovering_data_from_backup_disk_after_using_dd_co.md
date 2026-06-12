---
title: "recovering data from backup disk after using dd command"
date: 2020-06-30
forum: General Help
---

### Post by kshmr2 on 2020-06-30
It was first time, I was using "dd" to clone my old hdd(sdc1-150gb partition) to one of my ntfs partition(sda5-762gb partition) using command below

So sda5 already had aprrox 500gb data and was free 250gb+ aprrox, I did not know it would delete my important data

This was the command which I did

```
sudo dd if=/dev/sdc1 of=/dev/sda5 bs=64k
```

Now my old sda5 data is not not showing, didn't know that would happen tbh

I immediately disconnect the drive as soon as I saw my partition is not there which is barely few seconds.
I'm attaching the info here for you guys to see

```
/dev/sda2        96M   44M   53M  46% /boot/efi
/dev/sda8       386G   24G  343G   7% /home
/dev/sda5       150G   72G   78G  49% /media/kshmr/A4A27A23A279FA5E
/dev/sda4       460M  398M   63M  87% /media/kshmr/CC2CD5D52CD5BAA2
/dev/sda6       501G  282G  220G  57% /media/kshmr/One
/dev/sda7       108G   12G   96G  11% /media/kshmr/Two

Device          Start        End    Sectors  Size Type
/dev/sda1      923648    1945599    1021952  499M Windows recovery environment
/dev/sda2     1945600    2150399     204800  100M EFI System
/dev/sda3     2150400    2183167      32768   16M Microsoft reserved
/dev/sda4   208771072  209713151     942080  460M Microsoft basic data
/dev/sda5   209715200 1807775743 1598060544  762G Microsoft basic data
/dev/sda6  1807777792 2858448895 1050671104  501G Microsoft basic data
/dev/sda7  2858450944 3082911743  224460800  107G Microsoft basic data
/dev/sda8  3082911744 3907028991  824117248  393G Linux filesystem
/dev/sda9     2183168  208771071  206587904 98.5G Linux swap

```

So it seems my old data is still there but I'm not able to access it, anyone knows how can I recover or go back to previous state, any help would be appreciated, had really important data

---

### Post by VMC on 2020-06-30
try running [*testdisk*]("https://www.cgsecurity.org/wiki/TestDisk")

---

### Post by kshmr2 on 2020-06-30
seems like testdisk is searching for deleted data in new partiton that has been created and not the old partition

---

### Post by wildmanne39 on 2020-06-30
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by VMC on 2020-07-01
> **kshmr2 said:**
> seems like testdisk is searching for deleted data in new partiton that has been created and not the old partition

You have to direct testdisk what dev/drive to use.[IMG]https://www.cgsecurity.org/mw/images/Select_disk_update.png[/IMG]

---

### Post by Impavidus on 2020-07-01
You've overwritten the first 150GB of sda5, which is now a 762GB partition with a 150GB filesystem. 80% of your files (including partial files) may be recoverable using testdisk. They can be found between sector 509000000 and sector 1807775743. I've never needed testdisk myself; I prefer to rely on backups. The other 20% is gone.

I guess you now understand why dd is nicknamed data destroyer.

---

### Post by HermanAB on 2020-07-01
To be fair to the poor and frequently misunderstood dd - one can do the exact same destruction with several other utilities, for example cat.

---

### Post by sudodus on 2020-07-01
> **HermanAB said:**
> To be fair to the poor and frequently misunderstood dd - one can do the exact same destruction with several other utilities, for example cat.

This is true.

But it is a problem that many people use dd for this purpose, to write to drives (block devices). **I recommend to use tools *with a final checkpoint***, where the user gets information about the target device and can double-check that it is pointing to the correct drive before starting the cloning process.

**Disks** (gnome-disks) and **mkusb** and the **Ubuntu Startup Disk Creator** are such tools for cloning. A more advanced tool is **Clonezilla**, which creates an image that consists of a set of compressed image files, and that is smart enough to only copy used blocks (and skip free blocks in the file systems).

---

### Post by kshmr2 on 2020-07-01
> **VMC said:**
> You have to direct testdisk what dev/drive to use.[IMG]https://www.cgsecurity.org/mw/images/Select_disk_update.png[/IMG]

Yes sir I did select the drive which I wanted to recover the data from and unfortunately testdisk did not help me much, I used few tools like photorec and few windows tools, I was able to recover 30-40% of my data

---

### Post by kshmr2 on 2020-07-01
> **Impavidus said:**
> You've overwritten the first 150GB of sda5, which is now a 762GB partition with a 150GB filesystem. 80% of your files (including partial files) may be recoverable using testdisk. They can be found between sector 509000000 and sector 1807775743. I've never needed testdisk myself; I prefer to rely on backups. The other 20% is gone.

I guess you now understand why dd is nicknamed data destroyer.
 Yeah now I very well understood dd and also I did cancel the operation as soon as I started with cause I've this habit to check that data is going in right partition. Learned a lesson well :(

---

### Post by kshmr2 on 2020-07-01
> **sudodus said:**
> This is true.

But it is a problem that many people use dd for this purpose, to write to drives (block devices). **I recommend to use tools *with a final checkpoint***, where the user gets information about the target device and can double-check that it is pointing to the correct drive before starting the cloning process.

**Disks** (gnome-disks) and **mkusb** and the **Ubuntu Startup Disk Creator** are such tools for cloning. A more advanced tool is **Clonezilla**, which creates an image that consists of a set of compressed image files, and that is smart enough to only copy used blocks (and skip free blocks in the file systems).

Thanks for pointing relevant tools, will check them next time with proper care and backing up all my data first in safe place. Thank you :)

---

### Post by SeijiSensei on 2020-07-01
A safer method using dd is to write the image to a file.  Then you can decide where to extract it to later on.

```
dd if=/dev/sdX of=/home/me/sdx.img
```

---

### Post by Autodave on 2020-07-01
Another reason to have at least 2 backups.  I have 3 of them and one of them is kept at another location.

---

### Post by kshmr2 on 2020-07-01
> **SeijiSensei said:**
> A safer method using dd is to write the image to a file.  Then you can decide where to extract it to later on.

```
dd if=/dev/sdX of=/home/me/sdx.img
```
 
Yeah I released it later and did it, so might some data might be there too.

---

### Post by kshmr2 on 2020-07-01
> **Autodave said:**
> Another reason to have at least 2 backups.  I have 3 of them and one of them is kept at another location.

I did not had any hardware to backup those files, recently purchased external disk and I thought to backup old hdd first and I messed up. Learned a lot :)

---

### Post by ActionParsnip on 2020-07-01
Use your backups.... You do have backups of your important data......right?

---

### Post by HermanAB on 2020-07-01
Since I mentioned the friendly kitty cat:

dd if=/dev/sdX of=/home/me/sdx.img
cat /dev/sdX > /home/me/sdx.img

If you want to copy the whole file, from start to finish, then dd and cat are equivalent.
If you want to copy a specific number of bytes, starting at an offset, then dd comes into its own.

---

### Post by VMC on 2020-07-01
As long as its not NTFS file system, I prefer *fsarchiver* to *Clonezilla*. It also only copies used data, with the added benefit of restoring to a smaller drive. Plus its much simpler. Getting CZ to do that one has to jump through hoops.
Clone:
```
sudo ./fsarchiver -j6 -o savefs ubuntu.fsa /dev/sda6
```
Restore:
```
sudo ./fsarchiver restfs ubuntu.fsa id=0,dest=/dev/sda6
```

Edit: By the way CZ has *fsarchiver* already installed. Just drop to shell.

---

### Post by TheFu on 2020-07-01
Sorry, but any data that has been overwritten is gone.  Hopefully, you have backups.

The brilliance of dd is how dumb it is.  All it does is copy bytes from A --> B overwriting B in the process.  Period.  If you choose A and B correctly, it is a wonderful thing.  If you choose either A or B incorrectly, you get what you get.  Don't get B --> A wrong.  Brilliant and stupid.

If a disk is failing, there are dd-like tools that will try to get data that errors out of cat and dd, getting no more data.  To get passed any sector failures, check out **ddrescue** or **gddrescue**. Of course, before using any dumb tools like this, check out the manpage, understand the options, get the options in the correct order, and if they suggest a log file, CREATE A LOG FILE!

In Unix, everything is either a file or a process.  Everything that isn't in the process table can be treated like a file.  Files can be copied byte-by-byte into any other "file" which can be a device, a file, a directory, a file system, a partition, a whole disk, over the network (network devices are just files too). Everything is a file, right?  That's what all the examples above showing of=/path/to/some/file.img are doing.  With a raw file that is actually a partition + file system + files, you can directly mount that .img file as a file system ( thanks to everything being a file in Unix) and access the data that way when done. The image doesn't need to be re-located to a partition or a disk, just mounted. Tools like **kpartx** can make that easier to get the offsets and create dm-X devices for each file system that can be mounted.

And all of this is follows the Unix file and directory security model, so understanding those owner, group, permissions and ACLs is pretty handy when working in these non-standard, but useful, techniques.

Pretty flexible, huh?  When I first learned this stuff, my mind was blown, totally.

---

