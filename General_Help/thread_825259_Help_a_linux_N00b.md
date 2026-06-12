---
title: "Help a linux N00b"
date: 2008-06-10
forum: General Help
---

### Post by mickshifty on 2008-06-10
Hey everyone, i am a complte newbie to linux and im realy excited to learn about it. I have managed to create a dual boot, with linux and windows. my windows install is on a seperate drive. and i have ubuntu installed on my data drive. there is alot of data on that drive and i cannot access it. when i go into the properties of the "file system" it says, "some contents unreadable". im wondering if it is possible to get these files and how can i do it? thankyou very much for your help.

---

### Post by MythosLegend on 2008-06-10
If you are using windows and want to access files on a Linux partition, you may want a program called ext2ifs.

Ubuntu Hardy can read & write to ntfs partitions.

If this doesn't answer your questions, you have to be a bit more clear about your situation. 
Also providing the results of
```

sudo fdisk -L

```
may help.

---

### Post by iaculallad on 2008-06-10
> **MythosLegend said:**
> If you are using windows and want to access files on a Linux partition, you may want a program called ext2ifs.

Ubuntu Hardy can read & write to ntfs partitions.

If this doesn't answer your questions, you have to be a bit more clear about your situation. 
Also providing the results of
```

sudo fdisk -L

```
may help.

That would be (Small letter L):

```
sudo fdisk -l
```

---

### Post by MythosLegend on 2008-06-10
Oh boy. I'm starting to become forgetful.

---

### Post by mickshifty on 2008-06-10
sorry as i said i am very new to linux

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5db3c270

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3321    26675901    7  HPFS/NTFS
/dev/sda2            3322       24321   168682500    5  Extended
/dev/sda5            3322       24321   168682468+   7  HPFS/NTFS
administrator@michael-laptop:~$
```

---

### Post by MythosLegend on 2008-06-10
> **mickshifty said:**
> when i go into the properties of the "file system" it says, "some contents unreadable". im wondering if it is possible to get these files and how can i do it?

So you are using Ubuntu but can't read those files?

From your output, I only see one(first) hard drive. I don't see a linux partition (ext3 system) or a second hard drive (sdb). Did you post all of your output?

---

### Post by mickshifty on 2008-06-10
everything that was there i copied and pasted. i installed linux while i was in windows, i never formated any drives.

i can read the system files for ubuntu, but cannot read any of my other files. e.g. music, movie, applications that share that drive with ubuntu

---

### Post by mickshifty on 2008-06-10
i try and mount sda5 and it says this "mount: only root can do that"

---

### Post by MythosLegend on 2008-06-10
Oh. You installed ubuntu using Wubi.

If you want to mount with root permissions, you'll have to add sudo in front of your command.

Before you mount, you also need to make a directory.
Like 
```

sudo mkdir /media/disk

```

Then you can mount it.
```

sudo mount -t ntfs /dev/sda5 /media/disk

```

Now you can access the partition. It will be in location /media/disk.
You can unmount with
```

sudo umount /media/disk

```

---

### Post by mickshifty on 2008-06-10
ahhh yes, i didnt put the "sudo" in front when i mouted the drive. thankyou. ive actully uninstalled linux from my machine and im going to reformat the C:\ and make that the OS drive, if linux doesnt work out (which i highly unlikely) then i can always reinstall crappy windows. just wondering, if there is any linux start guides, i really want to learn as much as i can about linux, are there any sites or documentation i can read?

---

### Post by lemuriaX on 2008-06-10
Check these links out: 

[http://www.tuxfiles.org/](http://www.tuxfiles.org/) 

[http://www.psychocats.net/](http://www.psychocats.net/)

---

### Post by mickshifty on 2008-06-11
i know i am asking alot of questions, bu is there a general linu program that will allow me to run windows software in linux such as, adobe flash cs3, dreamweaver, windows games such as quake, world of warcraft, etc. thanks in advance

---

### Post by iaculallad on 2008-06-11
> **mickshifty said:**
> i know i am asking alot of questions, bu is there a general linu program that will allow me to run windows software in linux such as, adobe flash cs3, dreamweaver, windows games such as quake, world of warcraft, etc. thanks in advance

Try [WinE]("http://www.winehq.org/"). And you have to check out the [database]("http://appdb.winehq.org/") first if it supports the application you want to execute in Ubuntu.

---

### Post by lemuriaX on 2008-06-11
Also can look into running Windows as a virtual machine inside of Linux using Virtualbox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) or similar. Takes a lot of RAM though.

---

