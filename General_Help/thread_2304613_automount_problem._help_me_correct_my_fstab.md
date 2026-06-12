---
title: "automount problem. help me correct my fstab?"
date: 2015-11-28
forum: General Help
---

### Post by jackrussell007 on 2015-11-28
hi folks

i'm using ubuntu for all my home pc's for years now but am siill a newbie when it comes to troubleshooting simple stuff it seems. hope you can help me correct an automount problem>

I've got a second HDD in my pc which I want to automount for all users on boot up. Its the disk called movies(see below)

anyway I turned on the automount properties in the Disks utility but it doesnt seem to work. When I boot it gives an error, giving me the option to skip mounting or try for manual correction.

Any help would be appreciated, heres my fstab file.



# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6f08198b-06d6-465b-9898-cb978dde119e /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/disk/by-label/movies /mnt/movies auto nosuid,nodev,nofail,x-gvfs-show 0 0

---

### Post by Morbius1 on 2015-11-28
```
 /dev/disk/by-label/movies /mnt/movies auto nosuid,nodev,nofail,x-gvfs-show 0 0         
```
Edit /etc/fstab and remove the x-gvfs-show option and the comma that precedes it so that it looks like this:
```
 /dev/disk/by-label/movies /mnt/movies auto nosuid,nodev,nofail 0 0         
```

If you really want it to "show up" or whatever crazy thing Disks calls it then use the method that was working just fine for 40 odd years and change your mount point to /media/movies. Just don't set it to /media/your-user-name/movies. That&#8217;s for system use.

---

### Post by jackrussell007 on 2015-11-28
heres some extra info

when i try mount the disk manually i get this error. not sure if its beause I made a mess of my fstab file or do I have a dodgy disk?

thanks





Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/movies"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Bucky Ball on 2015-11-28
Please follow [Morbius1's advice]("ubuntuforums.org/showthread.php?t=2304613&p=13398167&viewfull=1#post13398167") and report back. If you're unsure how to go about it, just ask. ;)

---

### Post by jackrussell007 on 2015-11-28
sorry, I mustve forgot to refresh my browser before posting the second time. I missed morbius's post.

I edited as you advised and its working now. thanks very much for the help:)

(I did want it to show up in the interface so I changed the mount point as described)

Just beside the point.....how come it doesnt work when you edit the mount optinos in DISKS? Is it glitchy or did I do something wrong?
thanks

---

### Post by Bucky Ball on 2015-11-28
> **jackrussell007 said:**
> Just beside the point.....how come it doesnt work when you edit the mount optinos in DISKS? Is it glitchy or did I do something wrong?
thanks

Unsure. You might want to post another thread about that. 

Good you got the original issue fixed, though. Please see the first link in my post to help others (marking as solved won't close the thread to further discussion). Enjoy. :)

---

