---
title: "FAT32 formatted media cards read-only"
date: 2007-05-10
forum: General Help
---

### Post by Meir on 2007-05-10
My USB card reader built into my monitor works well under Feisty x64 except for this problem. I've tried all sorts of suggestions from different threads for manually mounting but no matter what it mounts read only. My FAT formated cards work just fine. Any help would be appreciated.

---

### Post by taurus on 2007-05-10
Maybe you need to remount it read-write permissions.  What's the output of this command from a terminal?

```
df -h
```

---

### Post by Meir on 2007-05-10
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              28G   19G  7.7G  71% /
varrun               1007M  260K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
procbususb           1007M  176K 1007M   1% /proc/bus/usb
udev                 1007M  176K 1007M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
lrm                  1007M   39M  969M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb2              46G  5.5G   39G  13% /home
/dev/hda1             115G   32K  115G   1% /media/hda1
/dev/hdb1              98G   76G   23G  78% /media/hdb1
/dev/hdb5              70G   17G   54G  25% /media/hdb5
/dev/sda1             280G  112G  169G  40% /media/sda1
/dev/sdc1             3.9G  178M  3.7G   5% /media/TRANSCEND
```
The transcend is the one with the problem.

---

### Post by taurus on 2007-05-10
Try

```
sudo umount /dev/sdc1
sudo mount -t vfat /dev/sdc1 /media/TRANSCEND -o iocharset=utf8,umask=000
ls -la /media
```

---

### Post by Meir on 2007-05-10
This is now very strange. If I run those commands and then try to modify something from the terminal then it works. If I then open Nautilus and attempt to modify something I get the Read-Only error. Is this a bug in Nautilus?

---

### Post by taurus on 2007-05-10
Maybe you need to close nautilus and open it up again after you mount that external drive by hand.

---

### Post by jerrylamos on 2007-05-10
By the way, easiest I've had to format USB pen drives is to run Gparted.  It may already be in Systems, Administration but if not Applications, Add/Remove can find the package to install.

On Gparted there's a little box on the top right hand corner, select the arrows to get the USB drive.  Select the USB line, you can unmount it, and format it selecting which format you want.  For Linux use only I do ext3.  Windows usually needs vfat F32 or F64 or whatever.

After that, exit Gparted, bring up Applications, Terminal and if ext2 or 3 formatted you can do an 
e2label /dev/sdc1 casper-rw
using whatever Gparted saw for /dev/???? and whatever label you wanted.

Thereafter, you can write to it as /media/casper-rw or whatever label you used.

The label I show is the one for Edgy or Dapper CD Live "persistent" mode.  "persistent" is busted on Feisty.

Cheers, Jerry

---

### Post by Meir on 2007-05-10
> **taurus said:**
> Maybe you need to close nautilus and open it up again after you mount that external drive by hand.

I didn't even have Nautilus open when I mounted the drive.

[QUOTE=jerrylamos]By the way, easiest I've had to format USB pen drives is to run Gparted. It may already be in Systems, Administration but if not Applications, Add/Remove can find the package to install.

On Gparted there's a little box on the top right hand corner, select the arrows to get the USB drive. Select the USB line, you can unmount it, and format it selecting which format you want. For Linux use only I do ext3. Windows usually needs vfat F32 or F64 or whatever.

After that, exit Gparted, bring up Applications, Terminal and if ext2 or 3 formatted you can do an
e2label /dev/sdc1 casper-rw
using whatever Gparted saw for /dev/???? and whatever label you wanted.

Thereafter, you can write to it as /media/casper-rw or whatever label you used.

The label I show is the one for Edgy or Dapper CD Live "persistent" mode. "persistent" is busted on Feisty.

Cheers, Jerry[/QUOTE]

It has to be fat32 because it too big for fat and my camera only supports fat and fat32.

Can anyone else duplicate the problem?

---

