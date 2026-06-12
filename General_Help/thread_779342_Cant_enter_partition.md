---
title: "Cant enter partition"
date: 2008-05-02
forum: General Help
---

### Post by zenithlt on 2008-05-02
Hi, I installed Ubuntu 8.04 in a new partition and i tried to run an other where is my all files and other stuff and it says: 

[[IMG]http://img176.imageshack.us/img176/3176/screenshotcx4.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshotcx4.png)

Any ideas whats wrong with that ?

---

### Post by Grishka on 2008-05-02
we won't know until you show the details. :)

---

### Post by MattBD on 2008-05-02
Not quite sure what you mean! Do you mean that you're dual booting with another operating system and you want to be able to access your files on that OS from your Ubuntu install?

---

### Post by zenithlt on 2008-05-02
> **MattBD said:**
> Not quite sure what you mean! Do you mean that you're dual booting with another operating system and you want to be able to access your files on that OS from your Ubuntu install?


no, i have 3 partition, in one Win Vista, other for downloaded files and third for Linux, and i want to access to downloaded files...

Details:

[[IMG]http://img205.imageshack.us/img205/7631/screenshotch3.th.png[/IMG]](http://img205.imageshack.us/my.php?image=screenshotch3.png)

---

### Post by MattBD on 2008-05-02
Right, I think I get you.
Ubuntu has supported the FAT filesystem for ages, and I've found Hardy has pretty good support for the NTFS filesystem, so you should be OK if it's formatted as either of those.
Can you run this to check what partitions you have and post the results here?
```
sudo fdisk -l
```
This will show what partitions you have on your system. For example, here's mine:
```
matthew@matthew-laptop:~$ sudo fdisk -l
[sudo] password for matthew:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008acac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         734        4864    33182257+  83  Linux
/dev/sda2             610         733      996030   82  Linux swap / Solaris
/dev/sda3               1         609     4891761   83  Linux

Partition table entries are not in disk order

```
It shows the three partitions I have on my laptop. If you post the results of this here, that should give a better idea of what's going on.

---

### Post by zenithlt on 2008-05-02
Here`s mine... any ideas?

```
drm@drm-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa74fa74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38913   210170362+   f  W95 Ext'd (LBA)
/dev/sda5           12749       35095   179499004    7  HPFS/NTFS
/dev/sda6           35096       38913    30668053+  83  Linux
drm@drm-desktop:~$ 



```

---

### Post by MattBD on 2008-05-02
Not sure why you don't seem to have a Linux swap partition, that's a bit strange! But anyway, it looks to me like /dev/sda1 is your Windows install. I expect you have a diagnostic partition as well, and if so I think that would be the /dev/sda2. So your /dev/sda5 appears to be the partition with the downloaded files.

Until Hardy, I wasn't able to mount HPFS/NTFS filesystems, but so far it's worked fine for me in Hardy, completely automatically. Basically, you need to mount the partition within your existing filesystem. You may want to have a look at [this link]("https://help.ubuntu.com/community/Mount") which describes the mount command, which you use to do this.

So, assuming that /dev/sda5 is the partition you want to mount, this is how you'd do it:
```
sudo mount /dev/sda5 /mnt

```

If that goes fine, you can then look in /mnt to find the partition you've just mounted. The /mnt directory is used for extra filesystem components like networked drives, so is a good place to mount that partition.

---

### Post by zenithlt on 2008-05-02
Is there any way to do something without format?  

```
drm@drm-desktop:~$ sudo mount /dev/sda5 /mnt
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /mnt ntfs-3g force 0 0
drm@drm-desktop:~$ mount -t ntfs-3g /dev/sda5 /mnt -o force
mount: only root can do that

```

---

### Post by Grishka on 2008-05-02
> **zenithlt said:**
> Is there any way to do something without format?  

```
drm@drm-desktop:~$ sudo mount /dev/sda5 /mnt
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /mnt ntfs-3g force 0 0
drm@drm-desktop:~$ mount -t ntfs-3g /dev/sda5 /mnt -o force
mount: only root can do that

```

man, do what it says. boot up vista, safely remove hardware and shut it down. maybe it crashed on you or something.

---

### Post by MattBD on 2008-05-02
> **Grishka said:**
> man, do what it says. boot up vista, safely remove hardware and shut it down. maybe it crashed on you or something.

That's what I was thinking too. But for the force option, you need to preface the command with sudo, like this:
```
sudo mount -t ntfs-3g /dev/sda5 /mnt -o force

```
But I'd leave that as a last resort. As Grishka said, it does look like your Vista install crashed or didn't shut down properly.

---

### Post by zenithlt on 2008-05-03
> **MattBD said:**
> That's what I was thinking too. But for the force option, you need to preface the command with sudo, like this:
```
sudo mount -t ntfs-3g /dev/sda5 /mnt -o force

```
But I'd leave that as a last resort. As Grishka said, it does look like your Vista install crashed or didn't shut down properly.

Yes now it works fine, thnx up man :) am bayme you know how to install Beryl ? I search in official site/wiki but in doesnt work now ;x

and how to install downloaded files like [COLOR="Red"]*.tar.bz2; *.tar.gz[/COLOR] ???

---

### Post by MattBD on 2008-05-03
For getting visual effects working, you might want to check out the documentation at [https://help.ubuntu.com/8.04/desktop-effects/C/](https://help.ubuntu.com/8.04/desktop-effects/C/) for guidance. Beryl isn't included in Ubuntu anymore as such - it's been replaced by Compiz Fusion. Assuming visual effects are working fine, if you want things like the cube, you need to install compizconfig-settings-manager.

As for .tar packages, again the documentation is pretty good at [https://help.ubuntu.com/8.04/add-applications/C/install-file.html#tarballs](https://help.ubuntu.com/8.04/add-applications/C/install-file.html#tarballs) but I would avoid installing things from tarballs (which is what .tar packages are known as) if you can. The repositories are pretty comprehensive these days, and [GetDeb]("http://www.getdeb.net/") is a good additional resource for getting extra software, so it's rare to need to install from a tarball. They can be a pain in the proverbial, so it's always best to see if you can find a .deb package (Ubuntu's native package format, which is also used by Debian, hence the name).

---

### Post by zenithlt on 2008-05-03
> **MattBD said:**
> For getting visual effects working, you might want to check out the documentation at [https://help.ubuntu.com/8.04/desktop-effects/C/](https://help.ubuntu.com/8.04/desktop-effects/C/) for guidance. Beryl isn't included in Ubuntu anymore as such - it's been replaced by Compiz Fusion. Assuming visual effects are working fine, if you want things like the cube, you need to install compizconfig-settings-manager.

As for .tar packages, again the documentation is pretty good at [https://help.ubuntu.com/8.04/add-applications/C/install-file.html#tarballs](https://help.ubuntu.com/8.04/add-applications/C/install-file.html#tarballs) but I would avoid installing things from tarballs (which is what .tar packages are known as) if you can. The repositories are pretty comprehensive these days, and [GetDeb]("http://www.getdeb.net/") is a good additional resource for getting extra software, so it's rare to need to install from a tarball. They can be a pain in the proverbial, so it's always best to see if you can find a .deb package (Ubuntu's native package format, which is also used by Debian, hence the name).


[Look here](http://www.youtube.com/watch?v=xC5uEe5OzNQ) i want that great animation when closing windows and those buttons on the top... Man u r greatest :guitar:

---

### Post by MattBD on 2008-05-03
I think the dock bar is Avant Window Navigator which you can install with the following:
```
sudo apt-get install avant-window-navigator awn-manager
```
AWN Manager will let you customise the dock. If you install compizconfig-settings-manager as well, that will let you customise Compiz Fusion to get it just right. Any problems, just post a query in Desktop Effects & Customization and someone should be able to help you.

---

