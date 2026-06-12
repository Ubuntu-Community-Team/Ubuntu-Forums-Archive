---
title: "Mount /home on NTFS (Gutsy)"
date: 2007-11-08
forum: General Help
---

### Post by skattman83 on 2007-11-08
I'm running Gutsy so I have read/write for my NTFS partitions. I have one NTFS partion set as my user directory in Windows, and I would like to set that same partition, or a directory within it, as my /home/ directory.  I tried this once, but it hosed my system, it said that it couldn't load because I didnt have permissions to my home directory.  I looked into it, and the ntfs partition mounts as belonging to root: plugdev.  I can't seem to change it to anything else though.  Does anyone know of a way to use a NTFS partition as your /home/ directory?

---

### Post by vanadium on 2007-11-08
ntfs does not work well with Linux because it is a proprietary file system. You must therefore keep your home partition on an ext3 volume. Within that home directory, you can create links to data directories on your ntfs volume, and thus, your ntfs volume will appear to belong to your home directory.

---

### Post by skattman83 on 2007-11-09
I installed the ext3 driver in vista and it works perfectly!  I'd like to move this same setup onto my desktop, but I was wondering if the driver will allow backup software like Retrospect Express to access the ext3 partition.

---

### Post by dabl on 2007-11-09
Because "/home" is part of the Linux standard filesystem, and NTFS is not on the list of standard filesystem formats, you're not going to be able to mount "/home" on a NTFS-formatted partition, AFAIK.

However, you can probably accomplish what you want to do by letting "/home" be a small directory within the same partition as the rest of the Linux filesystem, and making a separate "shared_data" partition, mounted in "/media", where your shared files can live, and it can be NTFS format if that's what you want.  :)

---

### Post by skattman83 on 2007-11-09
So I set up vista to use my ext3 partition that is mounted in ubuntu as home.  It doesnt seem like ext3 will allow me to mark files as hidden in windows though.  Is there any way to hide . files in windows?  I know I'm asking a lot of questions, but I would really like to just have one shared home directory rather than linux home and windows home.  Windows just doesn't seem to want to play nice with ubuntu.

---

### Post by skattman83 on 2007-11-09
Actually, I have another question about this.  Is it possible to defragment this partition, or is ext3 fragment-resistant enough not to worry about it?

---

### Post by dabl on 2007-11-09
Whoa -- don't even try it!

ext3 is inherently pretty resistant to degraded performance from file fragmentation. If you google the subject, there's lots been written about it.  Basically, ext3 is already fragmented by design, and works just fine that way  (I'm paraphrasing ...).

I don't think files that are "hidden" in Linux can be similarly hidden in Windows.  You really have two different systems in almost every way, and file-handling and viewing is also not the same.  And be careful that you don't overwrite any of the Linux hidden files while you're running Windows (that's why I suggested a separate data partition).  Your desktop and application settings are saved there. :)

---

### Post by skattman83 on 2007-11-09
> **dabl said:**
> Whoa -- don't even try it!

I don't think files that are "hidden" in Linux can be similarly hidden in Windows.  You really have two different systems in almost every way, and file-handling and viewing is also not the same.  And be careful that you don't overwrite any of the Linux hidden files while you're running Windows (that's why I suggested a separate data partition).  Your desktop and application settings are saved there. :)

Yeah, I think I'm just going to go back to having a media partition and a small home folder that stores my settings.  This is getting to be too big of a hassle.

---

