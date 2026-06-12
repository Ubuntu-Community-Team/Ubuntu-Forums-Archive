---
title: "Invalid mount option when attempting to mount the volume"
date: 2008-01-03
forum: General Help
---

### Post by revelationman on 2008-01-03
I have posted this before  

Today  I have done loads of reading on it  this site explains it is a bug 
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233)

It is a dvd-rw  that has my files and music on it and i get that error  

[25953.336000] UDF-fs: No VRS found

[25953.508000] ISO 9660 Extensions: Microsoft Joliet Level 3

[25953.608000] ISO 9660 Extensions: RRIP_1991A

[26056.356000] attempt to access beyond end of device

[26056.356000] hda: rw=0, want=3603748, limit=3603712

[26056.400000] UDF-fs: No partition found (1)

[26056.580000] Unable to identify CD-ROM format.

[26579.580000] attempt to access beyond end of device

[26579.580000] hda: rw=0, want=3603748, limit=3603712

[26579.644000] UDF-fs: No partition found (1)


I just want a fix that is all I am searching high and low   for the answer 
when i do  get  fix i am going too delete vista and just have Ubuntu 

So if anyone has a answer  please share I am sorry about  the posts on the same issue but this is driving me and many  people up the wall 

Thanks  

:guitar:

---

### Post by der_joachim on 2008-01-03
Does [this]("http://linux.derkeiler.com/Newsgroups/linux.redhat.misc/2005-04/0049.html") help? Aditionally, is it your automounter that fails or a manual mount?

---

### Post by revelationman on 2008-01-03
not too sound daft what command  

cheers

---

### Post by der_joachim on 2008-01-04
Oh just use the *mount* command. You can read a manual by opening a terminal and giving the command *man mount* for the zillion mount options. The command you probably have to use, would probably be something like:

```

sudo mount -t iso9660 -o ro /dev/hda /media/hda

```
The sudo command lets you run a command in superuser mode. You need this because you generally cannot mount manually as an ordinary user. The mount command falls apart in a few parameters:
* *-t iso9660* means that the file system is the standard iso9660 file system, which is most commonly used fol CDROMs and DVDs.
* *-o ro*. To be on the safe side, the DVD is mounted read-only. By their nature, CDROMs and DVDs are generally mounted read-only anyway. 
* */dev/hda* is the name of your DVD drive, as read in your first post and it is the source of the file system. 
* */media/hda* is the target directory in which your DVD is being mounted. This can be (almost) any folder, but /media is the de facto standard for external mounts in Ubuntu. Make sure that the mount point exists or you'll get an error.

Hope this helps.

---

