---
title: "2nd HDD Issues 16.04 LTS"
date: 2018-10-01
forum: General Help
---

### Post by brenneke on 2018-10-01
I have a second internal HDD on my system which has my Plex media files and documents. I have links on desktop for different document folders. When I restart, these desktop links are broken and I cannot access my Plex media files with Roku but if I select the 2nd HDD link I can access the drive and all the folders. 
how can I fix this up?

---

### Post by yancek on 2018-10-01
Do you have an entry for the partition(s) on the second hard drive in the /etc/fstab file so that it mounts on boot?

---

### Post by brenneke on 2018-10-01
Hmm....don't think so?

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=c49326a9-91c4-4a62-9f1a-5267c6f0a399 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=83a39169-ba85-495b-ad8c-2c0ee3425760 none            swap    sw              0       0


Please advise, thanks.

---

### Post by oldfred on 2018-10-01
If you linked it, you need to use same mount as default mount, or you will have to redo links.
Normally you create your own mount point and use that as your fstab entry.
I used to use the recommended UUID's for mounting, but am now switching to labels, so when I look at an entry I have some idea of what it is. If you only have one, you probably know what it is.

Generally you have to make mount point, add entry to fstab and give yourself ownership & permissions if Linux format partition. NTFS default mount only has permissions you give it when mounting. 

I typically use this:
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 
    

This is my data partition mount in fstab as an example. But I now use slightly different parameter.
```
# Entry for /dev/sdb4 on Asus AR:
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime,nofail,x-systemd.device-timeout=4 0 2

```

       [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by brenneke on 2018-10-01
I did some reading as you suggested and managed to fumble my way through getting this hard drive to mount properly on start up - thank you!

---

