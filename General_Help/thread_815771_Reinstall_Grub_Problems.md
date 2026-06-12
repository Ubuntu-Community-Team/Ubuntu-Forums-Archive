---
title: "Reinstall Grub Problems"
date: 2008-06-01
forum: General Help
---

### Post by SpenceMakesSense on 2008-06-01
So I tried reinstalling Grub Via terminal because Winblows deleted it. But when i tell it to install to a specific hard drive it claims it cant mount it. But I can mount the hard drive in nautilus. I have two hard drives and I cant install it on either. Any solutions or any different ways to install grub?

Also should mention im attempting to install via live cd of 8.04.

---

### Post by meierfra. on 2008-06-02
Tells us the exact commands you used  for reinstalling grub. Also post the output of 

```
sudo fdisk -l
```

and 

```
sudo grub
find /boot/grub/menu.lst
```
(both "l" are lowercase L)

---

### Post by SpenceMakesSense on 2008-06-02
whoops

---

### Post by SpenceMakesSense on 2008-06-02
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00030166

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbcbcd60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       47505   381583881   83  Linux
/dev/sdb2           47506       48641     9124920    5  Extended
/dev/sdb5           47506       48641     9124888+  82  Linux swap / Solaris
ubuntu@ubuntu:~$
``` 

```
grub> find /boot/grub/menu.lst
 (hd1,0)

grub> 
```

Now before I typed in the following command to install

```
 grub> root (hd0,0)

grub> setup (hd0,0)

Error 17: Cannot mount selected partition
```

Now after typing one of your commands I changed it up and thought it worked
```
grub> root (hd1,0)

grub> setup (hd1,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done. 
```

But when trying to boot it booted straight to windows again. I have my computer to automatically boot from my windows hard drive because when I had it set to boot from my Linux drive grub would give me errors that it couldn't mount selected partition but grub always seemed it work off my windows hard drive anyway. But I cant even install it on either now.

---

### Post by TeoBigusGeekus on 2008-06-02
Try supergrub
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by leito666 on 2008-06-02
This works for me a couple of days ago, I only have 1 hard drive so I made some changes in the next text:

Start with live cd, and go to console:

mkdir /home/ubuntu/mnt      ("mnt" is just a name for a folder, could be any)
sudo fdisk -l       (to see where is linux, in your case sdb1)
sudo mount -t ext3 /dev/sdb1 /home/ubuntu/mnt

sudo mount -o bind /dev /home/ubuntu/mnt/dev
sudo mount -o bind /proc /home/ubuntu/mnt/proc

sudo chroot /home/ubuntu/mnt    (becareful now, because any change will be over your real system and not from your Live CD)
grub-install --recheck /dev/sda   (grub will be in your windows hard drive)
grub-install /dev/sda

exit
exit

---

### Post by SpenceMakesSense on 2008-06-02
> **leito666 said:**
> This works for me a couple of days ago, I only have 1 hard drive so I made some changes in the next text:

Start with live cd, and go to console:

mkdir /home/ubuntu/mnt      ("mnt" is just a name for a folder, could be any)
sudo fdisk -l       (to see where is linux, in your case sdb1)
sudo mount -t ext3 /dev/sdb1 /home/ubuntu/mnt

sudo mount -o bind /dev /home/ubuntu/mnt/dev
sudo mount -o bind /proc /home/ubuntu/mnt/proc

sudo chroot /home/ubuntu/mnt    (becareful now, because any change will be over your real system and not from your Live CD)
grub-install --recheck /dev/sda   (grub will be in your windows hard drive)
grub-install /dev/sda

exit
exit

Worked Perfectly!
Thanks a bunch

---

### Post by meierfra. on 2008-06-02
Just in case you are curious what  went wrong with your first attempt to reinstall grub: You needed to use

sudo grub
root (hd1,0)
setup (hd0)
quit

---

