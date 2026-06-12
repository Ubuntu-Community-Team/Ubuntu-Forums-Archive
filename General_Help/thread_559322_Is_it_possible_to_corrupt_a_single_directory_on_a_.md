---
title: "Is it possible to corrupt a single directory on a volume???"
date: 2007-09-25
forum: General Help
---

### Post by prepstyles on 2007-09-25
Hello

I've got an ext3 volume that I use only for file storage (no: OS, swap, program installs, ect.)
On this volume I have a single directory that I can not access .... any program I use to access this directory just hangs.
The file explorer hangs if I double click on the directory ... <ls -l>  hangs, wine, azureus, utorrent ... take your pick they all just lock up and their processes become "uninterrupitible" according to the system monitor.

What I'm having a hard time understanding is how only a single directory can be acting this way on a volume that otherwise appears to be fine.....?
I'm not sure it matters but the directory is quite large ... several hundred gigs....

Any help is appreciated.


Cheers!

---

### Post by por100pre1 on 2007-09-25
> **prepstyles said:**
> I'm not sure it matters but the directory is quite large ... several hundred gigs....

Maybe you answer it yourself. Try using several folders instead of just one.

---

### Post by Alex1770 on 2007-09-25
> **prepstyles said:**
> Hello

...
The file explorer hangs if I double click on the directory ... <ls -l>  hangs, wine, azureus, utorrent ... take your pick they all just lock up and their processes become "uninterrupitible" according to the system monitor.
...

Cheers!

Being several hundred gigs is no problem.
Sounds like it might be a hardware fault. What sort of physical disk is it (e.g., internal hard
drive, USB drive, ...?).
You could try looking at the log files (/var/log/messages, /var/log/syslog, /var/log/kern.log)
to see if there are any recent messages referring to disk errors after doing an 'ls' on the
directory.

---

### Post by /etc/init.d/ on 2007-09-25
If there was a file system problem, messages from the driver will be in dmesg output.  As you try to access the directory, run dmesg and check for any messages from the ext3 driver.  That will rule out file system corruption.

I had a similar problem once (accessing the directory through graphical applications would hang), but getting to the directory through the CLI still worked.  I was able to copy my files out of the directory that way.

---

### Post by prepstyles on 2007-09-25
Thank you to everyone for the reply s!

> **Alex1770 said:**
> What sort of physical disk is it (e.g., internal hard
drive, USB drive, ...?).


The drive is an internal Serial ATA.


> **Alex1770 said:**
> You could try looking at the log files (/var/log/messages, /var/log/syslog, /var/log/kern.log)
to see if there are any recent messages referring to disk errors after doing an 'ls' on the
directory.


> **/etc/init.d/ said:**
> As you try to access the directory, run dmesg and check for any messages from the ext3 driver.  That will rule out file system corruption.


I took a look through the log files suggested ... most of which I can't understand but several of them had these lines about a kernel BUG appear in the files (at the end) after I tried to access the directory.

```

[  562.282798] ------------[ cut here ]------------
[  562.282800] kernel BUG at fs/ext3/namei.c:384!
[  562.282803] invalid opcode: 0000 [#1]
[  562.282804] SMP 
[  562.282807] Modules linked in: isofs udf binfmt_misc r ... <Whole Ton of other Modules> ...

```


I'm now wondering if this is a kernel problem that could just resolve itself with the next update or recompile ... wishful thinking most likely ....

I tried accessing the directory with an XP install from another drive (using the open source ext2 driver) ... the directory opened however I didn't' try and move or open any of the files
... what I think I will do is try and copy the contents of the corrupted directory elsewhere (on the drive) and delete the newly emptied directory,  and see if that doesn't improve things.

I would appreciate any more feedback if it comes to mind.

Cheers!

---

### Post by por100pre1 on 2007-09-25
If you want to try another kernel, try adding a low latency kernel. It is a kernel for using Jack and other audio stuff, but it can be installed on any Feisty system:

```
sudo aptitude install linux-lowlatency
```

it won't remove your current kernel.

---

### Post by Alex1770 on 2007-09-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
					> **prepstyles said:**
> Thank you to everyone for the reply s!
...
I'm now wondering if this is a kernel problem that could just resolve itself with the next update or recompile ... wishful thinking most likely ....

I tried accessing the directory with an XP install from another drive (using the open source ext2 driver) ... the directory opened however I didn't' try and move or open any of the files
... what I think I will do is try and copy the contents of the corrupted directory elsewhere (on the drive) and delete the newly emptied directory,  and see if that doesn't improve things.

I would appreciate any more feedback if it comes to mind.

Cheers!

This looks like the bug reported here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177)

Apparently this results from using a Windows ext2/3 driver which corrupts the ext3 filesystem. The Linux ext3 driver  is meant to be able to cope with this kind of problem, but doesn't in this case.

If your data is important to you and you are able to copy it off to somewhere safe, then I'd suggest doing that before doing anything else.

Then you could try to see if fsck (file system check and repair) cures it. This has to be run on an unmounted volume. One way to do this (I think) is
```
sudo touch /forcefsck
```
Then it should run a check on the next reboot. (Be around then in case it asks you for options, like autorepair.)

---

### Post by prepstyles on 2007-09-26
Hey Alex looks like that was the case!

> **Alex1770 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
					

This looks like the bug reported here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177)

.....

Then you could try to see if fsck (file system check and repair) cures it. This has to be run on an unmounted volume. ...
Then it should run a check on the next reboot. (Be around then in case it asks you for options, like autorepair.)

Yea when I booted today fsck forced a scan on the volume in question (something to do with the number of times it was mounted without a check).  fsck reported that:

```
HTREE directory inode 1933313 has an invalid root node 
HTREE INDEX CLEARED
```

The scan restarted and completed, now all seems well .... I had considered fsck but was not sure how to run it on a mounted volume ... the automated one during boot proved quite useful.

Thanks again to everyone for the feedback.

Cheers!

---

