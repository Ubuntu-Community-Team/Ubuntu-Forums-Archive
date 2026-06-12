---
title: "How to move files between Ubuntu and Windows"
date: 2023-11-09
forum: General Help
---

### Post by satimis on 2023-11-09
Hi all,

It is possible moving files btw Ubuntu 22.04 (Linux) drive or ext 4 drive and Windows drive (Win10/Win11).  I have done it long time ago but unfortunately I forgot the steps and software used.

Please advise.  Thanks in advance.

Regards

---

### Post by yancek on 2023-11-09
You can mount a windows filesystem from Linux and you should be able to read/write to it if you have ntfs-3g installed which should be on Ubuntu.  It is not a good idea to write to and modify 'system' files on windows but having a data partition for windows ntfs should not be a problem.  You need to either put a proper entry in /etc/fstab and you can find any numberof examples of how to do this with various options.  The link below to ubuntu.com gives a pretty good description of it.  If the windows drive is always attached, this would be the way to go.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by satimis on 2023-11-09
> **yancek said:**
> You can mount a windows filesystem from Linux and you should be able to read/write to it if you have ntfs-3g installed which should be on Ubuntu.  It is not a good idea to write to and modify 'system' files on windows but having a data partition for windows ntfs should not be a problem.  You need to either put a proper entry in /etc/fstab and you can find any numberof examples of how to do this with various options.  The link below to ubuntu.com gives a pretty good description of it.  If the windows drive is always attached, this would be the way to go.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Thanks for your advice.

**[COLOR="#FF0000"]Drives installed on this PC[/COLOR]**
PCIe 3.0 NVMe SSD 2TB - running Ubuntu 22.04
SATA6 SSD 1TB - running Windows 10 Home
WD drive 4TB - solely for storage, ext4 format without OS installed

I need moving files amongst them while running Ubuntu 22.04 or Windows 10 Home.  What will be an easy and simple setup?

Thanks

Regards

---

### Post by MAFoElffen on 2023-11-09
Is it a temporary external drive or a partition of an internal drive? I remember you have quite a setup, but do not remember the specific details of it.

If permanent, and you are using that NTFS partition as the go-between, then mount it permanently from your fstab, to a created permanent mountpoint that is convenient for you to get to. I usually suggest for people to either create a /data folder off from root (/) or if you are the only user on that computer, then to create a folder off from your user home folder... 

Then in your fstab file, set the mount options similar to this
```

UUID=828C01738C016351  /Media_H  ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw  0  0

```

---

### Post by satimis on 2023-11-09
> **MAFoElffen said:**
> Is it a temporary external drive or a partition of an internal drive? I remember you have quite a setup, but do not remember the specific details of it.

If permanent, and you are using that NTFS partition as the go-between, then mount it permanently from your fstab, to a created permanent mountpoint that is convenient for you to get to. I usually suggest for people to either create a /data folder off from root (/) or if you are the only user on that computer, then to create a folder off from your user home folder... 

Then in your fstab file, set the mount options similar to this
```

UUID=828C01738C016351  /Media_H  ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw  0  0

```
Hi MAFoElffen,

Thanks for your advice.  It is a permanent external drive, not a partition of an internal drive.

I have both external drive and internal drives, solely for data storage on ext 4 format without OS installed.  The external drive is for sharing data amongst PCs instead of via router.  They have been running for years.  I have 3 PCs.

I think that I was looking for a wrong solution in the beginning.  I should look for 2 solutions;
1) While running Ubuntu 22.04 how to make it connecting Windows drive, copying files from and to the later.

2) While running Windows how to make it connecting Ubuntu 22.04 drive and the storage drives, copying files from and to them.

I have done it long time ago but unfortunately I forgot their setup.

Regards

---

### Post by MAFoElffen on 2023-11-09
Technically, there is no such thing as a "permanent" external drive (except for rack servers, SANS, LUNS, iSCSI, etc... But logically/functionally, I can see where you mean that it is USB and you always have it plugged in... LOL

Same.
.
.
.
.
.
Meaning: Add the mount to the fstab file. Then it is always mounted there, from whatever OS you boot. Add it to your other Ubuntu's fstab also. (I remember you had two of the same version at one time.) The permissions and access are set and always the same... Nothing else "special" to do after that. Then you just treat is as another folder...

Right?

---

### Post by HermanAB on 2023-11-10
Caution: Windows needs to be completely shut down before mounting and writing to its disk with Linux.  By default Windows suspends leaving its disks in an unknown state.  Safest is to transfer files using a SD card or USB widget.

---

### Post by satimis on 2023-11-10
Hi all,

I found an easy way copying files between "Ubuntu 22.04" and "Windows 10 Home" on this PC, without any software installed.

**[COLOR="#FF0000"]Steps as follows;[/COLOR]**

Start "Ubuntu 22.04"

-> Files -> Documents 
select and right-click a file to be copied to 'Windows 10 Home'
-> Copy to ...

(still on Files)
-> Other Locations
-> Select and click "Windows 10 Home" drive
-> click "Documents and Settings"
-> click username
-> click Documents
-> Select

That is all.  The file is copied to this folder "Document".

Copying a file from "Windows 10 Home" to "Ubuntu 22.04" is the same but in other way round.  It is NOT necessary to start "Windows 10 Home"

Regards

---

### Post by yancek on 2023-11-10
While booted into Ubuntu, you can copy from/to a windows filesystem.  I wasn't sure from your original post if you wanted to copy files from a booted windows OS or not.  If that were the case, I don't believe windows has that capability as a default system does not read or write to a Linux filesystem.  There is 3rd party software which should be able to do this.  Doesn't seem this is a concern in our case so...

---

### Post by satimis on 2023-11-10
> **yancek said:**
> While booted into Ubuntu, you can copy from/to a windows filesystem.  I wasn't sure from your original post if you wanted to copy files from a booted windows OS or not.  If that were the case, I don't believe windows has that capability as a default system does not read or write to a Linux filesystem.  There is 3rd party software which should be able to do this.  Doesn't seem this is a concern in our case so...
My need is quite simple;
1) Copy file from Ubuntu 22.04, which is running, to Windows 10 Home, which is not running. 
2) Copy file from Windows 10 Home, which is not running, to Ubuntu 22.04, which is running.

Now I can do them without third party solfware

Regards

---

### Post by oldfred on 2023-11-10
Mount options for an internal drive should be adjusted for any drive than can be removed.
If for any reason you disconnect an USB drive then you will have issues booting as fstab cannot find drive. It may timeout or lock up system.

[https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd](https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd)
Either systemd-automount or autofs can be used. 
[https://manpages.debian.org/stretch/systemd/systemd.automount.5.en.html](https://manpages.debian.org/stretch/systemd/systemd.automount.5.en.html)
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections

---

