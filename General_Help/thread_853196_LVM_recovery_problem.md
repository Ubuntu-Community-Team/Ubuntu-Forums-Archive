---
title: "LVM recovery problem"
date: 2008-07-08
forum: General Help
---

### Post by mwk on 2008-07-08
Due to a string of stupid actions on my part, I've ended up in a situation whereby I have a disk with LVM partitions that were created by a previous operating system, which are refusing to be accessed by the current one. 

There's a single volume group of 87.37GB, there are two physical volumes that add up to that much, and there's a single logical volume that contains 21.84GB of data, which is the exact amount used in the physical volumes.

lvscan tells me that '/dev/system/var' (the only logical volume) is active, but when I try and mount it, it repeatedly responds 'you must specify the filesystem type'. I've run through everything on the list I recognise, because I don't actually remember what it was formatted as (though I'd expect ext3 like the rest of the drive), but none of them work.

Any ideas?

---

### Post by j0nny55555 on 2008-07-27
This is just my guess and I am fairly new at this, you needed to do a back up of your LVM config with something like:

```
vgcfgbackup
```

would allow the backup of an existing LVM volume settings.  Now there is a folder that is created when the LVM runs that maintaines this information as well - and if I remember some of my reading correctly it actually puts the parts in 

```
/etc/lvm
```

or something like that.  You will need to reset the meta tags on the hard drives to allow them to look like what they used to, because they have probably been new UUID or they might've been formatted - which for your case, I hope not.

Does

```
vgscan
```

or

```
pvscan
```

come back with anything?  I read about the lvscan - and there is a chance your new OS doesn't know where to look until it has tried to initialize all the drives.  Again, I'm new to supporting linux, but have done it for Windows and Macs my whole life.  I figure after working with linux for about 6 years I had better start trying to support it so I can be more familiar with it.

---

