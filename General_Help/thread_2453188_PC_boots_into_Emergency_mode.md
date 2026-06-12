---
title: "PC boots into Emergency mode"
date: 2020-11-04
forum: General Help
---

### Post by bhcarpe on 2020-11-04
I am running Ubuntu 18.04.5 x64.  I just installed a 4TB hard drive in my PC and formatted it to ext4.  I restarted my computer, and now it always goes to emergency mode.  I was getting a lot of acpi messages, so i turned acpi off and rebooted.  It went to emergency mode.  I used journalctl -xb and now the only 2 messages I see in red are> No caching mode page found
Assuming drive cache: write throughThese are referring to the 4TB drive.  I have a 4TB Desktop USB drive that I installed earlier with no issues,   Any thoughts on how I can escape this vicious cycle?

---

### Post by bhcarpe on 2020-11-05
bump

---

### Post by bhcarpe on 2020-11-05
Okay, after going through the journal for hours, I saw that my NFS clients were not being mounted.  That is the ONLY thing I saw that seemed to be a possible cause.  So I commented those mounts out in fstab.  Glory be, the OS booted up.  Now I have no idea why that worked.  There have been many times in the past when the NFS server was not started and the OS booted fine.  In any case, I'll take it.  I won't close this thread because I didn't solve anything.  I was desperate, so that was the last in a long list of things I tried.

---

### Post by oldfred on 2020-11-07
I have seen several posts with similar issues.
I do not have any network mounts so do not know all the details.
They keep improving boot time, but time for external drives to come up to speed or be mounted has not really changed.

[https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd](https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd)
[https://manpages.debian.org/stretch/systemd/systemd.automount.5.en.html](https://manpages.debian.org/stretch/systemd/systemd.automount.5.en.html)
Either systemd-automount or autofs can be used. 
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections
use noauto if mount issues
[https://askubuntu.com/questions/1047109/how-can-i-delay-mount-of-secondary-internal-hard-drive-on-boot?noredirect=1#comment1710066_1047109](https://askubuntu.com/questions/1047109/how-can-i-delay-mount-of-secondary-internal-hard-drive-on-boot?noredirect=1#comment1710066_1047109)

---

### Post by bhcarpe on 2020-11-11
Today I had a system update with a new kernel.  After the update, the system needed to be rebooted.  Once again I ended up in Emergency mode.  Once again, I commented out my fstab entries for the NFS shares and the system booted properly.  I made other changes to my fstab as well.  Here is my fstab before any changes:```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4b8651b0-a37a-4d23-9d9e-333f01408c56 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
UUID=7677ace4-168d-4f94-87fe-d5a5c1372ff5 none            swap    sw              0       0
#Entry for /dev/sdb1
UUID=f3676964-3fac-407e-88f9-9b345f83c687 /media/Data_Three    ext4    errors=remount-ro 0 1
#Entry for /dev/sdc1 :
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e /media/Data_Two     ext4    errors=remount-ro 0 1
#Entry for /dev/sdd1 :
UUID=3573b59f-77c9-460d-9a29-9f6730954125 /media/Data_One    ext4    errors=remount-ro 0 1
#Entry for /dev/sde1 :
UUID=53262b5b-1827-46cc-88f3-9b7e858464a2 /media/Data        ext4    errors=remount-ro 0 1
#Entry for External USB Data Backup Drive
UUID=c4f82388-713a-4b9a-9f50-e36446e17520 /media/butch/Ubuntu_Data_Back    ext4    errors=remount-ro 0 1
#Entry for NFS Server on drive g on cp2
192.168.1.111:/media/brenda/Ubuntu_Data_Back /nfs/Ubuntu_Data_Back nfs_netdev,vers=3 0 0
#Entry for NFS Server shared documents on cp2
192.168.1.111:/media/brenda/cp2_data /nfs/cp2_shared_docs nfs _netdev,vers=3 0 0 0
``` and here it is after changes:```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4b8651b0-a37a-4d23-9d9e-333f01408c56 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
UUID=7677ace4-168d-4f94-87fe-d5a5c1372ff5 none            swap    sw              0       0
#Entry for /dev/sdb1
UUID=f3676964-3fac-407e-88f9-9b345f83c687 /media/Data_Three    ext4    errors=remount-ro 0 1
#Entry for /dev/sdc1 :
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e /media/Data_Two     ext4    errors=remount-ro 0 1
#Entry for /dev/sdd1 :
UUID=3573b59f-77c9-460d-9a29-9f6730954125 /media/Data_One    ext4    errors=remount-ro 0 1
#Entry for /dev/sde1 :
UUID=53262b5b-1827-46cc-88f3-9b7e858464a2 /media/Data        ext4    errors=remount-ro 0 1
#Entry for External USB Data Backup Drive
UUID=c4f82388-713a-4b9a-9f50-e36446e17520 /media/butch/Ubuntu_Data_Back    auto nosuid,nodev,nofail,x-gvfs-show 0 0
#Entry for NFS Server on drive g on cp2
192.168.1.111:/media/brenda/Ubuntu_Data_Back /nfs/Ubuntu_Data_Back nfs vers=3,auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
#Entry for NFS Server shared documents on cp2
192.168.1.111:/media/brenda/cp2_data /nfs/cp2_shared_docs nfs vers=3,auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```I got the options for local attached USB Hard Drives and the options for NFS shares from here [https://www.techrepublic.com/article/how-to-properly-automount-a-drive-in-ubuntu-linux/](https://www.techrepublic.com/article/how-to-properly-automount-a-drive-in-ubuntu-linux/)
and here [URL="https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-18-04"]https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-18-04
[/URL]

---

### Post by bhcarpe on 2020-11-11
I couldn't get the last link to let me type regular text.  I want to add it remains to be seen if this will work.  If so, I will close this thread.  If not, I'll keep it open.

---

