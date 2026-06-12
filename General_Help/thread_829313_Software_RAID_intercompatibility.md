---
title: "Software RAID intercompatibility"
date: 2008-06-14
forum: General Help
---

### Post by srilowha on 2008-06-14
I've been reading various sources about RAID configurations and it seems like software RAID is not only cheaper, but also seems to have good enough performance to serve basic needs (plus I think it's built into ubuntu).  One thing I've been wondering though is how 'proprietary' the storage is.  By this I mean, if I had just my data across three disks for example with RAID 5, and later decided I needed to move them all to another machine, would I be able to access that data?  Is it enough the OS on the other machine to use the same file system?  Or would it have to be the same OS through which I created the configuration?  Basically I'm trying to figure out how much flexibility there is once you set this up.

With a single NTFS drive for example you could pop it in and out of Windows systems, and with how good NTFS support is now, into Linux systems as well and still be able to read data.  How do things change once your data is managed by a software RAID?  I assume the software adds its own specific meta-data for distributing the writes and for recovery purposes, but does that follow some global standard?

This is essentially the same question framed in a different context: if I had ubuntu installed on a single disk with no replication or protection of any sort, and all of my data was on separate disks together in RAID 5, and the OS is corrupted or that disk dies, would I be able to just replace it, install fresh, and still access the data?

I'm just trying to learn more about this all works and plan ahead for when I come to actually implement this.  Thanks in advance for any explanations you can provide.

---

### Post by fjgaude on 2008-06-14
Yes, yes.

I've taken my four drives, raid5, to other motherboards and all that had to be done, using Ubuntu 7.10, 8.04, was to install mdadm and then run this command:

```
sudo mdadm --assemble --scan
```

That's it. I've done such about five times over the last two years.

Now you should study the man mdadm pages to understand just how complex raid is first.

---

