---
title: "Backing a Image of Ubuntu?"
date: 2008-02-19
forum: General Help
---

### Post by UK-Wobbie on 2008-02-19
I like to backup my Ubuntu desktop computer on to a server, But i like to backup as a image file!
Are there any tools what will yet users to backup Ubuntu and make a Image file of the system?

Thanks

---

### Post by jeffus_il on 2008-02-19
I don't really know what you mean by an image file ...
If you want a copy of your system so that your can restore it from a backup in case you disk goes, for instance, then:[LIST]
[*] Boot from the LiveCd and simply copy your partition/s to the backup machine.
[*] If you want the data to be in an achive(1 file) then you can use tar or a gui archiving program.[/LIST]It may be sufficient  to back up only the /home folder as most of the data resides there( depending on your system) and the rest of the install can be done from the LiveCd.

---

### Post by kpkeerthi on 2008-02-19
See [Backup ubuntu using partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by seventhc on 2008-02-19
I'm not hijacking this thread, but I also have a question about a certain type of backup. I already have a complete back up of my *home directory* but I would like to know if there is a way, perhaps a command that would back up the entire system to a second hard drive. I mean a hard drive in an external enclosure and if the first hard drive fails, I could just swap out the drive and boot into the system.
So basically it would be a full working system, not just certain files.

---

### Post by cdenley on 2008-02-19
You can't backup a hard drive while running ubuntu off of it. Assuming your second drive is at least as large as your first, you can boot to a livecd, then run
```

sudo bash
cat /dev/hda>/dev/hdb

```
where hda is the original, and hdb is the copy.

---

### Post by seventhc on 2008-02-19
@ cdenley
would running that command from the hard drive give a working copy of ubuntu?

---

### Post by UK-Wobbie on 2008-02-19
> **jeffus_il said:**
> I don't really know what you mean by an image file ...
If you want a copy of your system so that your can restore it from a backup in case you disk goes, for instance, then:[LIST]
[*] Boot from the LiveCd and simply copy your partition/s to the backup machine.
[*] If you want the data to be in an achive(1 file) then you can use tar or a gui archiving program.[/LIST]It may be sufficient  to back up only the /home folder as most of the data resides there( depending on your system) and the rest of the install can be done from the LiveCd.

A IMAGE is a copy of the System  like ISO or BIN format :)

---

### Post by UK-Wobbie on 2008-02-19
I like something what is easy and easy to use

---

### Post by philinux on 2008-02-19
This is a good project

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

### Post by cdenley on 2008-02-19
> would running that command from the hard drive give a working copy of ubuntu?
> You can't backup a hard drive while running ubuntu off of it.
I'm not sure if the command would fail or not. Even if it didn't, you're copying a device while you're writing to it, and this can cause the copy to be corrupt.

> A IMAGE is a copy of the System like ISO or BIN format
Those formats are used for cd's and dvd's. They are raw data dumps. The difference with a hard drive is that there is no unused data on a cd or dvd (left over capacity is ignored and unreadable). If you want a raw data dump, you can use the cat or dd commands. Partimage will give you the same results as a raw data dump, but saves time and space by ignoring unused data and using compression. Archiving your files will copy your files and permissions, but will not allow you to recreate your partition table and stuff.

---

### Post by UK-Wobbie on 2008-02-19
> **cdenley said:**
> I'm not sure if the command would fail or not. Even if it didn't, you're copying a device while you're writing to it, and this can cause the copy to be corrupt.


Those formats are used for cd's and dvd's. They are raw data dumps. The difference with a hard drive is that there is no unused data on a cd or dvd (left over capacity is ignored and unreadable). If you want a raw data dump, you can use the cat or dd commands. Partimage will give you the same results as a raw data dump, but saves time and space by ignoring unused data and using compression. Archiving your files will copy your files and permissions, but will not allow you to recreate your partition table and stuff.

I know the formats are CD and DVD formats! But saying the size of my system and burning time lol I be better putting the ISO on to the server, And when i like to reinstall i can use a tool to get the ISO from the server and reinstall Ubuntu

---

### Post by UK-Wobbie on 2008-02-19
> **philinux said:**
> This is a good project

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

Thanks i have a look at that :)

---

### Post by jeffus_il on 2008-02-21
Then if you are not going to burn it, use a regular copy, using a livecd, and you can optionally tar (archive into one file) and compress it. If you want a gui, use the Archiver in Gnome. If you want the command line syntax post here.

---

