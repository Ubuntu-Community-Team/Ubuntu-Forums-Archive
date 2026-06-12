---
title: "Native cloning software in Ubuntu"
date: 2021-03-16
forum: General Help
---

### Post by robertsaron on 2021-03-16
I spent hours and hours and hours looking for a system I could easily install into Ubuntu 20.04 LTS, that would clone my hard drive. And then I could use that software to restore the hard drive with all it's partitions and files. 

There are allot options out there for live DVD/CD/USB that you can boot to, and then clone your drive. I would love to see something natively built into ubuntu for for cloning and restoring. 

Does anyone know of any software that is easy to install into linux, that can clone the drive, at its sector level if needed. And then restore that image just as easily? This is where Windows and MAc rule, there are so many options for both on this front, that are easy to come by and use.

---

### Post by daniewicz on 2021-03-16
from the command line you can use dd

---

### Post by C.S.Cameron on 2021-03-16
I use Gnome-Disks to make an image file, (.img).
This image file is a clone of a disk, that can be restored using Disks, mkusb, Startup Disk Creator, dd, Etcher, Rufus, Win32DiskImager, etc. The image file can be compressed to save space.

---

### Post by TheFu on 2021-03-16
I use **dd** or **ddrescue**.  dd is installed on every Unix system that I know. That includes every Linux.

The real problem with cloning is with corruption cased by the file systems being active. That makes it extremely inconvenient.

---

### Post by Impavidus on 2021-03-17
If there are writes to files while you're cloning the hard drive, the clone may be corrupt as a random selection of the writes will be included in the clone. That's why you normally clone while running a live system. There are more advanced filesystems that allow you to create a snapshot, but as clones aren't that useful, only few people do so.

---

### Post by robertsaron on 2021-03-17
I looked into DD, and I am not proficient enough with command line to use it. :( I will look into gnome disks. Thanks everyone. Can I use gnome disks or DD while the system is running?

---

### Post by TheFu on 2021-03-17
> **robertsaron said:**
> I looked into DD, and I am not proficient enough with command line to use it. :( I will look into gnome disks. Thanks everyone.

Generally, dd uses 3 parameters.

```
sudo dd if={source} of={target}  {options}
```
so .... 
```
sudo dd if=/dev/sda  of=/dev/sdZ   bs=4M
```

sda is the entire HDD, so the target should be an entire HDD that is at least the same size as sda.
sda1 is the first partition on sda.  If you want to clone bit-for-bit sda1 to sdZ3, use:
```
sudo dd if=/dev/sda1  of=/dev/sdZ3   bs=4M
```
The partition, sdZ3, must already exist and be sized to be the same or larger than sda1.

dd is very dumb.  It copies all the bytes from A --> B.  Period.  If you have the wrong "B", then that will be bad, but the same can be said for every other cloning tool.  If you get A and B backwards, then whatever B has gets shoved into A, wiping it completely.  But the same is true for every other cloning tool.

dd stops when there is any problem.  This is why people use **ddrescue**.  ddrescue will try to copy all the data is can. The most common use for dd/ddrescue is when a HDD is failing and no backups exist.  With dd, when a dead sector is hit, it stops.  With ddrescue when a dead sector is hit, it tries a few times, then skips it for the next sectors and continues.

ddrescue has 3 parameters too, but it cares about the order of the parameters. This can cause issues for many people not used to ordered parameters.  But if you use cp and mv, then it is pretty clear.
```
sudo ddrescue --force {source} {target}  /path/to/logfile
```
If the source and target are backwards, it will be a bad day, just like with dd.
The --force option is there as a reminder to carefully double and triple check the {source} and {target} order.
The logfile is how ddrescue keeps track of already failed sectors so it can come back and try again.  It can also be used to pick up where a cloning was being performed later.

That's a bunch of words to say
[LIST=1]
[*]all cloning software is dangerous. Get the parameters wrong and it will be a bad day.
[*]dd/ddrescue are very dumb AND very powerful.  Both can copy files, partitions, whole HDDs or SSDs.  
[*]On Unix systems, everything is a file, so taking an image file and shoveling it into a flash drive is trivial. dd is how we make Ubuntu Install flash drives.  Take the .iso file and shovel it into the flash drive. For example:
```
sudo dd if=/tmp/ubuntu-mate-20.04.2-amd64.iso  of=/dev/sdj  bs=4m
```
Very simple.
[/LIST]

There are specialized tools, like mkusb, for creating flash boot drives from ISO files which can also create NTFS and EXT4 partitions of different sizes during the process of putting a bootable Ubuntu ISO onto the flash media too.

There are other tools for cloning disks and partitions into compressed files.  fsarchiver is one.  Any cloning software needs to be booted from a different OS.  Some people have a small cloning boot partition on their systems just for this as a backup method.  Many people, myself included, see cloning as a very poor backup/recovery method for many reasons.  But we understand when you are new that worries about "getting everything you need" outweigh the efficiencies of using file-based backups with allow for quick, daily, automatic, versioned backups.

---

### Post by HermanAB on 2021-03-17
On UNIX, any utility that can copy a file, can copy a disk.

So there are many:
dd, cat, head, tail, nc... the list goes on and on.

The best ones are cat and dd.

For example:
$ sudo cat /dev/sda > /dev/sdb

Can't be any simpler really.

---

### Post by C.S.Cameron on 2021-03-17
> **robertsaron said:**
> I looked into DD, and I am not proficient enough with command line to use it. :( I will look into gnome disks. Thanks everyone. Can I use gnome disks or DD while the system is running?

You want to run Disks from a Live USB, not from the running system you want to duplicate.

---

### Post by TheFu on 2021-03-17
> Can I use gnome disks or DD while the system is running?
No imaging/cloning software can be safely run from the same OS you are trying to image/clone ... most of the time. Chances are if you are asking that question, then you didn't install more advanced volume management and file system management solutions which would allow it. These can't be added later. They must be installed during /prior to the OS installation.

Sorry.

You'll want to create a Try Ubuntu live flash drive, boot into the Try Ubuntu environment - which is basically a CDROM-like situation, then use whatever backup/cloning tool you want.  Expect this to take hours.  Doing it the most efficient way possible, I cloned a 4TB HDD last year and it took 26 hours ... so about 150GB/hr on my system.  USB will probably be slower.  SSD will be much faster.

---

### Post by HermanAB on 2021-03-18
26 hours... Yawn... That is why it is usually best to backup your data and re- install.  There are ways to automate the install.  The advantage is that it will handle differing hardware.

---

