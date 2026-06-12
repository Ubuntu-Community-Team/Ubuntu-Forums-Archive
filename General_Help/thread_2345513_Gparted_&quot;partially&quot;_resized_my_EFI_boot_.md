---
title: "Gparted &quot;partially&quot; resized my EFI boot partition (images show)"
date: 2016-12-04
forum: General Help
---

### Post by finny388 on 2016-12-04
I believe this partition was created by Win10 when I installed it.

My main distro right now is kubuntu on another partition.

the /boot/efi partition got filled (100 mb - unusual?) so with gparted I successfully downsized Win10 as one action. Then expanded the /boot/efi to 400mb as another. But it came with the same error that this Check did (at the bottom) ("we're working on it"?):

[IMG]http://i.imgur.com/rX3jsEa.png[/IMG]

Now the OS complains it is full but gparted says it is 400mb and full (?)

df -h (Size 96, Used 96, Avail 0):
[IMG]http://i.imgur.com/KtcDAxb.png[/IMG]

gparted (Unused 0?):
[IMG]http://i.imgur.com/Bqa9VHI.png[/IMG]

How can I rectify this?

Thanks

---

### Post by oldfred on 2016-12-05
I only have Ubuntu installed an use 28MB of my 500MB and I have multiple installs of Ubuntu, but grub only uses one, so each install I back up inside my ESP.
My one dual boot uses 54MB of the 100MB that Windows normally provides.

So surprised its full, but I do suggest 300 to 500 as a size for the ESP if you partition in advance.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

      
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by finny388 on 2016-12-05
I will boot into Boot-repair tonight and post the boot-info results.

Thank you so much. I don't however see what this has to do with booting so much as drive space allocation.

---

### Post by finny388 on 2016-12-05
Could be full b/c I have been having trouble installing KDE Neon and have done it several times lately. (doesn't seem to like nVidia)

---

### Post by gedakc on 2016-12-05
The exclamation point beside the partition graphic in GParted indicates there was an issue reading the file system usage in the partition.  To learn more either double-click on the partition, or select the partition and use the "Partition -> Information" menu item.

---

### Post by finny388 on 2016-12-05
Here is my boot info:
[http://paste.ubuntu.com/23586747/]("http://paste.ubuntu.com/23586747/")

I got the partition info in gparted, it told me to Check which is what the orig post shows:
[IMG]http://i.imgur.com/viPcBIv.png[/IMG]

why gparted can't repair it I don't understand

---

### Post by oldfred on 2016-12-06
I think you need chkdsk from Windows or dosfsck from Ubuntu.

Your sdc5
>     Boot sector info:  According to the info in the boot sector, sdc5 has 
                       204800 sectors.. But according to the info from the 
                       partition table, it has 819199 sectors.
 Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

Have you moved drives around in SATA ports?
Grub in UEFI mode only installs to an ESP on sda. But your ESP is not sdc5?

But it looks more like you manually moved your ESP?
# /boot/efi was on /dev/sda2 during installation
#UUID=94B3-07F4  /boot/efi       vfat    defaults        0       1
UUID=A4E0-0DEF	/boot/efi	vfat	defaults	0	1

---

### Post by finny388 on 2016-12-06
i bought a new ssd a while ago that I wanted to become main.

I was having trouble installing kde neon so I was trying sda and sdc for boot/grub during installs.  I didn't know that would create a second ESP.

maybe I should nuke and pave the whole thing.

I want 
main ssd (960gb) as sda
100gb - main distro
100gb - alt distro
remainder (700gb) - win10

2nd ssd 250gb as sdb
divided into 8 partitions for trying out other distros

i'll try chkdsk or dosfsck first though

---

### Post by oldfred on 2016-12-06
I have multiple full Ubuntu installs on sdb and external flash drives. And no matter what I say about installing grub in UEFI boot mode to sdb or external it overwrites my /EFI/ubuntu folder in sda. I quickly learned to back up my ESP, but with Ubuntu it only changes the /EFI/ubuntu/grub.cfg that is a configfile to full grub.cfg in the install. So now it just edit/backup that.

---

### Post by gedakc on 2016-12-06
> **finny388 said:**
> Here is my boot info:
[http://paste.ubuntu.com/23586747/]("http://paste.ubuntu.com/23586747/")

I got the partition info in gparted, it told me to Check which is what the orig post shows:
[IMG]http://i.imgur.com/viPcBIv.png[/IMG]

why gparted can't repair it I don't understand

Unfortunately you've run into a limitation in the libparted library that GParted uses to resize FAT16/32 file systems.

See [Bug 649324 - failure to move / resize fat32 partitions less than 256 MB in size]("https://bugzilla.gnome.org/show_bug.cgi?id=649324").

---

### Post by finny388 on 2016-12-06
i bought a new ssd a while ago that I wanted to become main.

I was having trouble installing kde neon so I was trying sda and sdc for boot/grub during installs.  I didn't know that would create a second ESP.

maybe I should nuke and pave the whole thing.

I want 
main ssd (960gb) as sda
100gb - main distro
100gb - alt distro
remainder (700gb) - win10

2nd ssd 250gb as sdb
divided into 8 partitions for trying out other distros

i'll try chkdsk or dosfsck first though

---

### Post by finny388 on 2016-12-06
Thanks gedakc, so nice to verify a bug

Old Fred, how do you back it up? Throughout this I haven't been able to even view it. Win10 doesn't see it in explorer (but does in Disk Mgt), and ubuntu doesn't see it until I mount it but then I don't have the rights to view it.

I would love to learn more about uefi, linux boot process so that I can manage my partitions and installs like I used to: with mastery :-|:-)
do you know any good resources?

---

### Post by karl96 on 2016-12-06
Efi partition that size is very unusual, if you have a separate boot partition it can sometimes get full due to kernel upgrades keeping old files but EFI should never be full.

You could try resizing the partition with
```
parted
```

```
print
``` will show you the partition layout

you can then use ```
 resize 
``` to resize your partition, e.g to resize partition 1 ```
 resize 1 100 300 
```

If you don't have the rights to view it you may be able to bypass it with ```
 chroot +x /dev/sda(n) 
``` but I don't know if that'll work
 
probably best to do it indirectly by making a directory on ```
mnt
``` e.g ```
mkdir /mnt/boot mount /dev/sda(n) /mnt/boot chroot +x /mnt/boot 
```

---

### Post by oldfred on 2016-12-06
I have not seen it recently, but we have seen cases where some corruption or setting in the ESP could not be fixed. 
So solution was copy entire FAT32 to another location, delete partition, recreate FAT32 with boot flag and restore files. Reinstall of grub not normally required, but when gpt's GUID changes UEFI may have issues and you then need to use efibootmgr to recreate entries or houseclean old entries. Or full reinstall grub which will recreate UEFI entries.

---

### Post by finny388 on 2016-12-08
> **oldfred said:**
> I have not seen it recently, but we have seen cases where some corruption or setting in the ESP could not be fixed. 
So solution was copy entire FAT32 to another location, delete partition, recreate FAT32 with boot flag and restore files. Reinstall of grub not normally required, but when gpt's GUID changes UEFI may have issues and you then need to use efibootmgr to recreate entries or houseclean old entries. Or full reinstall grub which will recreate UEFI entries.

sorry oldfred but can you walk me through this?

---

### Post by oldfred on 2016-12-09
Do you have backup procedures? You should anyway.
Or another drive, flash drive, DVDs or someplace not on current drive?
 [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 

Then just backup the ESP, if you can see the files in it. 
If you can see file from Nautilus, you can just use it to copy & paste to another drive. Just copy each folder like 
       /efi/Boot 
/efi/ubuntu 
      /EFI/Microsoft
And any others.

If you cannot read it, then you have major corruption. Try chkdsk from Windows, but you then have to manually mount it as Windows does not normally show the ESP.

---

### Post by finny388 on 2016-12-11
Cannot work with the mounted folder. Does mean I cannot view/back it up?```
$ sudo mount /dev/sdc5 /mnt/boot
mount: /dev/sdc5 is already mounted or /mnt/boot busy
       /dev/sdc5 is already mounted on /boot/efi
       /dev/sdc5 is already mounted on /mnt/boot
$ chroot +x /mnt/boot/
chroot: cannot change root directory to '+x': No such file or directory
$ cd /mnt/boot/
bash: cd: /mnt/boot/: Permission denied
$ ls /mnt
boot
```

---

### Post by oldfred on 2016-12-11
If from inside your install, you may have it set with permissions that do not let you mount it.
Boot-Repair always changes those if it can. I manually change it before leaving the installer.

       # /boot/efi was on /dev/sda1 during installation
#14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
# 16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

   Change the parameter to from umask=0077 to defaults. 
   sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
or
sudo nano /etc/fstab
sudo mount -a 

I found even remounting does not change current mount, but had to reboot, so now I change as soon as I install from the installer.

---

### Post by finny388 on 2016-12-11
changed fstab to defaults
rebooted
then chown'ed the folder and I can read it.
It is now backed  up.

Seems the boot-repair log folder (/boot-sav/log) contains 67MB of logs. (folders in this e.g. format: 2016-11-29__01h59boot-repair39, each about 3.8MB)

Knowing this has not corrupted does it change your advice. This dual partition state is confusing. Desktop says 100MB and full, gparted says 400MB.

I wonder if making some space in the folder (deleting logs) could help gparted resize it. Worth a shot...

---

### Post by finny388 on 2016-12-11
trying to chown boot-sav but Operation is not Permitted

:(

---

### Post by oldfred on 2016-12-11
Can you not just sudo rm delete it. Just make sure not to add any extra spaces in an rm command you may delete something else.

---

### Post by finny388 on 2016-12-11
```
sudo rm -rf 2016*
```

did the trick

thanks

will try gparted resize soon

---

### Post by finny388 on 2016-12-11
gparted failed again to Check. 100MB bug I guess

so I logged into Kubuntu and ran KDE Partition Manager. It was successful and said it reclaimed the space but no change - desktop still sees 100MB. hmm...

---

