---
title: "Folders inexplicably moved"
date: 2018-04-26
forum: General Help
---

### Post by oliviabaq on 2018-04-26
Hello. I'm using Ubuntu 17.10 and have been using Ubuntu for a number of years. 
A few days ago, for some reason, (it might have been after an update ran) every subfolder within folders such as Documents, Music, Pictures etc. were moved out of that folder (so out of Documents, Music, Pictures etc) into the Home folder. I am pretty sure I had turned my laptop off and when I turned it on again, everything was out of place.
I moved one of these folders (School) back into its original folder (Documents) but later (after an update or just after turning the computer on again) that folder (School, with all its subfolders) had been moved out of Documents and back into Home. But there was a new weirdness: I recently created a new file and saved in "school" once it had been moved back into Documents; so what happened was that everything in School moved back to Home, except for this file, which sits in a copy of the School folder in Documents by itself. 
None of my files have disappeared, but this is very weird and I can't figure out why it's happening. Does anyone have any idea what could be doing this?

Thanks!
Olivia M. B.

---

### Post by oldfred on 2018-04-26
If you have a separate partition for /home which is mounted by fstab and that partition is corrupted so it does not mount during boot, system will make a new /home with defaults.

Post these:
 lsblk -f
cat /etc/fstab

---

### Post by oliviabaq on 2018-04-28
```
lsblk -f

NAME   FSTYPE    LABEL UUID                                   MOUNTPOINT
loop0  squashfs                                               /snap/libreoffice/
loop1  squashfs                                               /snap/libreoffice/
loop2  squashfs                                               /snap/core/4206
loop3  squashfs                                               /snap/core/4486
loop4  squashfs                                               /snap/vlc/158
loop5  squashfs                                               /snap/libreoffice/
loop6  squashfs                                               /snap/skype/30
loop7  squashfs                                               /snap/skype/22
loop8  squashfs                                               /snap/wavebox/104
loop9  squashfs                                               /snap/wavebox/106
loop10 squashfs                                               /snap/skype/23
loop11 squashfs                                               /snap/core/4407
loop12 squashfs                                               /snap/vlc/190
loop13 squashfs                                               /snap/wavebox/103
sda                                                           
&#9492;&#9472;sda1 LVM2_memb       s8cWc6-4n6l-eGrJ-g0Nf-uzYx-8Bd4-im6tWn 
  &#9500;&#9472;ubuntu--vg-root
  &#9474;    ext4            30ab9536-779b-4f82-ae0d-2d832b49fdd3   /
  &#9492;&#9472;ubuntu--vg-swap_1
       swap            aed9915f-960a-43d6-a16f-ab0221e19060   [SWAP]
sr0     
```                                                      

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
```

---

### Post by oldfred on 2018-04-28
That is a LVM - logical volume manager install.
Do you also have full drive encryption?

Do not know LVM, but you may need fsck or other repairs.
       Ubuntu 16.04.3 LTS - correct fsck method for encrypted LVM? 
[https://ubuntuforums.org/showthread.php?t=2375964](https://ubuntuforums.org/showthread.php?t=2375964)

I have this in my notes, but do not know if complete:

 sudo apt-get update && sudo apt-get install lvm2 cryptsetup
df -h
sudo blkid
sudo fdisk -l
sudo pvdisplay
sudo lvdisplay
mount
sudo vgscan --mknodes
sudo vgchange -ay
sudo e2fsck -f /dev/ubuntu-vg/root  <--example use your device

As per fstab, so is this your device?
/dev/mapper/ubuntu--vg-root

---

