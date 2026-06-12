---
title: "ubuntu USB and NTFS Partition Read-Only"
date: 2018-04-16
forum: General Help
---

### Post by muhammadhussain95 on 2018-04-16
I have dual boot with windows and an NTFS partition that I use to save files. I save files on this partition so I can access them through both OS's. I auto-mounted the ntfs partition until recently where ubuntu would only start in emergency mode because of this. However when I did fix the emergency issue, any usb, windows partition and the extra partition are now read-only. I've tried solutions posted on similar threads but none seem to work. All disks mount to /media/owner. Running ls -al yields this result:

```

drwxrwx---+ 6 owner owner  4096 Apr 16 14:25 .
drwxr-xr-x  3 root  root   4096 Dec 18  2016 ..
dr-x------  1 owner owner 12288 Apr 15 17:36 Data Disk
dr-x------  1 owner owner  4096 Apr 16 03:09 E0DE8BAFDE8B7D12
```

"Data Disk" is the ntfs partition and "E0DE8BAFDE8B7D12" is a USB stick. Is there anyway I can add write permissions to fix the issue?

Thanks in Advance

---

### Post by oldfred on 2018-04-16
Are you dual booting with Windows 8 or 10?
That has fast start up setting that is really just  hibernation and then the Linux NTFS driver will not mount read/write to prevent damage.
And Windows will turn fast start up back on with updates which may be in background and you do not even know it changed your settings.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

I also like to label all my partitions, particularly any of those I may not auto mount with fstab (and its mount point) and label all external flash drive partitions. Then they are mounted by label, not UUID. And I avoid spaces as you have to escape or quote names/labels with spaces. I use under_score, CamelCase or justonename.
 
```
fred@Z170N:~$ lsblk -f
NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                         
&#9500;&#9472;sda1 vfat   ESP      D966-440A                            /boot/efi
&#9500;&#9472;sda2 ext4   xenial   5c1e1a3f-261f-4da5-a0c2-8f479b3039de /
&#9500;&#9472;sda3 ext4   ISO      ab916e15-8a74-4d6e-a0b1-32718a505dc7 
&#9492;&#9472;sda4 ext4   bionic   c29fc361-ea05-420b-b919-850aeef65dd4 
sdb                                                         
&#9500;&#9472;sdb1 vfat   ESP_B    F496-1330                            
&#9500;&#9472;sdb2 ext4   bionic_b 06cdd4fd-6a03-4880-9021-7febff21e4b1 
&#9500;&#9472;sdb3 ext4   ISO_b    c395f36d-5e02-4913-a904-e336054b2eff 
&#9500;&#9472;sdb4 ext4   backup_b dd4e4a2e-4785-4441-91b0-28234b98e625 
&#9500;&#9472;sdb5 ext4   server   b76dc590-99a3-4e34-af35-e0dd43507232 
&#9500;&#9472;sdb6 ext4   data     f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7 swap            3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9500;&#9472;sdb8 ext4   zenial_b 6c042846-fc6c-4f5b-80fc-7aa678cf09b7 
&#9492;&#9472;sdb9 ext4   Fedora   5326d262-26af-4b38-a523-b0f4d261f1a4
sdc                                                         
&#9500;&#9472;sdc1 vfat   ESP_USB  2A41-9535                            
&#9500;&#9472;sdc2                                                      
&#9500;&#9472;sdc3 ext4   usb_root 69333549-6680-4072-bdcb-94e333ab044c /media/fred/usb_root
&#9492;&#9472;sdc4 ext4   data     fd68f44e-743d-473d-8e25-5653f862ec24 /media/fred/data 
```

---

### Post by Impavidus on 2018-04-16
How do you mount the partition? If it's automatically mounted at boot time, that's probably by using /etc/fstab – which is the proper way to do this. /media/username is where removable drives get mounted automatically by the desktop environment. Maybe not ideal for mounting via fstab, to prevent interference.

Can you show```
cat /etc/fstab
```

---

### Post by muhammadhussain95 on 2018-04-16
Thanks for the reply.

I dual boot with window 10.

Windows did turn fast boot back on, didn't think it would do that. I've been using windows recently for some coursework and have been hibernating it instead of shutting down so I think this might have contributed to this issue. 

My laptop is quite old so it use MBR instead of UEFI.

---

### Post by muhammadhussain95 on 2018-04-16
@Impavidus

Until the Ubuntu emergency (about 3 weeks ago) issue I was having, it was mounted through fstab however I've been using windows (about a month) and hibernating it instead of shutting it down.It started to cause issues with the mount point therefore I removed it. This is what fstab looks like currently:

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=75b7dba4-d91f-4f5e-a13e-aa0f6055c70b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bb160a02-d486-40d1-bd4d-b750c3eb69d9 none            swap    sw              0       0 
```

---

### Post by yancek on 2018-04-16
> hibernating it instead of shutting it down.It started to cause issues with the mount point therefore I removed it.

I'm not sure if I am reading this correctly but, if you had an entry in fstab for windows and left it hibernated, no LInux system will mount it and it will be inaccessible from Linux.

---

### Post by muhammadhussain95 on 2018-04-16
> **yancek said:**
> I'm not sure if I am reading this correctly but, if you had an entry in fstab for windows and left it hibernated, no LInux system will mount it and it will be inaccessible from Linux.

I should've clarified, the partition (that was) in fstab is not the windows partition, it is an extra partition that I use to store file which I can access between both operating systems.
I'll posted the contents of fdisk -l below to avoid further confusion:

```
Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1  *         2048    1026047    1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048  312795687  311769640 148.7G  7 HPFS/NTFS/exFAT
/dev/sda3       312797184  314572799    1775616   867M 27 Hidden NTFS WinRE
/dev/sda4       314576894 1465147391 1150570498 548.7G  5 Extended
/dev/sda5       314576896  598575103  283998208 135.4G 83 Linux
/dev/sda6       598577152  630575103   31997952  15.3G 82 Linux swap / Solaris
/dev/sda7  *    630577152  823515135  192937984    92G 83 Linux
/dev/sda8       823517184 1465147391  641630208   306G  7 HPFS/NTFS/exFAT

```

The partition that i'm referring to is the 306GB one.

---

### Post by oldfred on 2018-04-16
Grub does not use boot flag, but Windows requires it on the primary NTFS partition that has its boot files.
Remove boot flag from sda7 with gparted, Windows repair disk or command line.
But I do not think that is related to your issues, but would be to directly boot Windows from MBR when you need to make repairs.

The Linux NTFS driver will not mount NTFS that is hibernated (or if it needs chkdsk). And then grub cannot see it either to add Windows boot stanza to grub menu.

---

### Post by muhammadhussain95 on 2018-04-16
@oldfred

Thanks, I've sorted the flags out. 

Some good news, I managed to get the 306GB partition (NTFS one) to read and write. ntfs-3g somehow got uninstalled (I used this for mounting the ntfs partition) so I can now read and write to it. However USB's are still read-only.

I also just realised I'm on 16.10 and not 16.04 although I don't think this could be the cause of it?

Any suggestions on what I could try?

---

### Post by oldfred on 2018-04-16
You need to update. 16.10 is obsolete.
 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) 

Best to stay with LTS versions, 16.04 is the current LTS version, but 18.04 will be out by the end of April.

What format are USB?
If NTFS can you read from Windows?
If ext4 did you give yourself ownership & permissions?

---

### Post by muhammadhussain95 on 2018-04-17
@oldfred
The USB’s are ntfs. They work fine in windows.

---

### Post by oldfred on 2018-04-17
Then they should work in Linux.
You should just be able to click in Naulitus left panel on flash drive. Mine just automounts, but it is ext4 and I have not mounted NTFS for ages.
I do label partitions, so it mounts under label, not UUID so I know which is which.

But fast start must be off in Windows as that leaves all mounted NTFS hibernated. And you need to always correctly unmount flash drive before removing it, both Windows & Linux.

---

### Post by muhammadhussain95 on 2018-04-25
I managed to fix the issue by updating to 17.10 from 16.10. Thank you

---

