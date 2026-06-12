---
title: "Using Live CD to access the hard drive"
date: 2007-06-19
forum: General Help
---

### Post by Luft on 2007-06-19
I have a friend who has a PC with Windows XP on it.  He somehow corrupted the OS to the point he can't recover.  He would like to gain access to his hard drive so that he can copy some personal files.

I was thinking that he might be able to run Ubuntu 7.04 live CD and mount his hard drive.  Then he could use a flash drive and copy his files over.

The thing is I don't know how to mount a drive when the live CD is booted.

Can anyone gvie me clear and detailed information on how he may be able to save his files in this way?

Thanks. :confused:

---

### Post by mikewhatever on 2007-06-19
A quick google search turned up nice results, here they are 
[http://www.google.co.il/search?q=ubuntu+mount+ntfs+live+cd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+mount+ntfs+live+cd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
The following one looks very clear and simple 
[http://ubuntuforums.org/showthread.php?t=310076&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=310076&highlight=ntfs)
You may need to use /dev/sda syntax  instead of /dev/hda, depending on what live cd you have and which hdd.

---

### Post by merlinus on 2007-06-19
From a terminal:

```

sudo fdisk -l
sudo mkdir /mnt/windows
sudo mount -t ntfs dev/hda1 /mnt/windows

```

The first command will show the partitions,  The third assumes windows is hda1.

if the filesystem is fat32, substitute that for ntfs.

Then use Nautilus to browse to that folder.

-merlin

---

### Post by confused57 on 2007-06-19
Another excellent guide for mounting Window's filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

---

### Post by mdurham on 2007-06-20
The simplest way is Places->Computer and right click on the desired partition->mount

---

