---
title: "Incorrect File System size?"
date: 2007-09-20
forum: General Help
---

### Post by BuilderQ on 2007-09-20
In Xubuntu 7.04, I open the file manager on "File System", then choose "Properties" from the right-click menu. I am given this information:

**Size:** 126573 items, totalling 5.5 GB
**Volume:** 2G Volume
**Free Space:** 320.6 MB

Since my hard drive in only about 4.2 GB, and Xubuntu is on a 2 GB partition ... what does the Size value mean?

---

### Post by kidders on 2007-09-22
Hi there,

Perhaps you calculated the total size of more than one filesystem? If you want to find out how much space your root filesystem is taking up, try **df -h /**

---

### Post by BuilderQ on 2007-09-22
That gives me ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             1.9G  1.5G  319M  83% /
``` which looks about right. What do you mean by "more than one file system" though? What other than the hard drive is supposed to make up the "Size"?

---

### Post by kidders on 2007-09-22
Almost anything, really. Unless you specifically instruct them *not* to traverse filesystems, many tools calculate space consumption by blindly descending into every subdirectory, starting at whatever point you specify. Since you started in '/', absolutely every mounted filesystem will probably have been taken into account, including any optical discs, network shares, RAM filesystems, pseudo-filesystems (eg /proc, /sys), and so on ... whatever happened to be there at the time.

---

### Post by BuilderQ on 2007-09-22
Okay, thanks.

Now all I have to do is figure out what Baobab's thinking when it tells me that my total filesystem capacity is only 3.7 GB ... :lol:

---

### Post by kidders on 2007-09-23
That seems about the right ballpark for a 4.2GiB hard disk. Have you got some extra disks space it should be taking into account?

---

### Post by BuilderQ on 2007-09-23
I would have thought that a 4.2 GB hard drive should have a 4.2 GB capacity. I think Baobab is ignoring swap space, but that alone wouldn't account for the difference. From [http://www.marzocca.net/linux/baobab.html](http://www.marzocca.net/linux/baobab.html), I note that it says "Baobab will not count the /proc dir, nor any file size that is not related to a 'plain' file, so symlinks, character blocks, device blocks will not be part of the directory size." Maybe that explains it. Also, I wonder if the same meaning of GB is used in the different measurements I have seen.

Is there a program which can present a simple, complete representation of hard disk usage (like the drive C pie graph in Windows)?

---

### Post by kidders on 2007-09-23
> **BuilderQ said:**
> I would have thought that a 4.2 GB hard drive should have a 4.2 GB capacity.That's not the case. You're forgetting about the space consumed by your partition table, filesystem metastructures, and a variety of other things. On top of that, there's always a significant difference between a filesystem's theoretical and real capacities, since it's very unlikely your files will fit neatly into filesystem blocks. For example, one wouldn't expect the capacity of a freshly formatted 1GiB USB flash disk to be precisely one gigabyte. Furthermore, by the time the disk is full (ie there are zero bytes of free space on it), there may well be quite a bit less data on it than the initial format capacity suggested would fit.

> **BuilderQ said:**
> I think Baobab is ignoring swap spaceThat's certainly true. Including it wouldn't be meaningful. Much of the additional difference might perhaps be accounted for by taking reserved blocks into account. Typically, about 5% of most filesystems is reserved for use by root, depending on the settings used when creating them.

> **BuilderQ said:**
> Baobab will not count the /proc dirThe contents of that directory don't physically exist, so I imagine Baobab's developers figured including it would be misleading ... like /sys, it doesn't take up any disk space.

> **BuilderQ said:**
> Also, I wonder if the same meaning of GB is used in the different measurements I have seen.Not necessarily! For some reason, people (and programs) seem to still use "GB" when they mean "GiB" ... which can get confusing.

---

### Post by BuilderQ on 2007-09-23
Thanks for your detailed response.

> **kidders said:**
> That's not the case. You're forgetting about the space consumed by your partition table, filesystem metastructures, and a variety of other things.
Hmm ... I had thought that space consumed by anything was space consumed from the disk capacity.
> **kidders said:**
> Including it wouldn't be meaningful. Much of the additional difference might perhaps be accounted for by taking reserved blocks into account. Typically, about 5% of most filesystems is reserved for use by root, depending on the settings used when creating them.
I'm not sure that including swap space would be unmeaningful. There are terminal commands to reveal the amount of swap space, so why not a graphical representation?

Running **sudo baobab** gives me some slightly different figures for a few folders but still the same total filesystem capacity. By the way, I note that folder sizes and number of items are reported differently if I check in the Thunar file manager or Baobab ...

---

### Post by atlfalcons866 on 2007-09-23
are you using ext3? if so you lost 5% of your space because ext3. ext3 reserves 5% of the space for the superblock and inodes.

---

### Post by BuilderQ on 2007-09-23
> **atlfalcons866 said:**
> are you using ext3? if so you lost 5% of your space because ext3. ext3 reserves 5% of the space for the superblock and inodes. The Xubuntu partition is ext3.

Running **sudo fdisk -l | grep Disk** I find that the hard disk size is 4303 MB. Is there a GUI program which can tell me the same? Or do they all interpret size in their own way?

---

### Post by kidders on 2007-09-24
> **BuilderQ said:**
> Running **sudo fdisk -l | grep Disk** I find that the hard disk size is 4303 MB. Is there a GUI program which can tell me the same?Any disk partitioner (whether it has a GUI or not) should be able to tell you that. For most people's purposes, it's not a useful figure though ... technically speaking, it doesn't tell you much about how much data you can actually store on your disk.

You may find utilities that use the same data source as **df** more informative. Those figures are the equivalent of the little pie charts you mentioned, that Windows shows you in filesystem "Properties" dialogs. I suppose it all depends on what you're looking for.

---

