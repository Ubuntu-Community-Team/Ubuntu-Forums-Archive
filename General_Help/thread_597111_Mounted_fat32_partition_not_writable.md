---
title: "Mounted fat32 partition not writable?"
date: 2007-10-30
forum: General Help
---

### Post by bailout on 2007-10-30
I have just installed gutsy. I have a fat32 partition for data that I share with XP. On previous releases I have set this up to mount by editing the fstab with this line;
/dev/sd5   /media/Data   vfat   user,fmask=0111,dmask=0000   0   0

This time I used the disk management in kubuntu system settings and although I can see it I can't write to it despite having ticked 'make writable'. The line that has been added to fstab is as follows;
/dev/sda5 /home/me/Data auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

(ignore the different location)

What is stopping the drive being writable, despite appearing to have a rw tag, and is there any reason why I shouldn't just copy the old line I used to use. The 'arguments' used in the new gennerated line are completely different.

thanks

---

### Post by kosmic on 2007-10-30
Why the hell you have this maks = fmask=0111 ?? It will make your drive only Read and execute..

---

### Post by Steve1961 on 2007-10-30
I use Ubuntu rather than Kubuntu so automount my fat32 partition directly from the Gnome sidebar rather than using an fstab entry.  However, once mounted the mount command gives this output:

/dev/sda5 on /media/Documents type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

When using fstab with other distros I always use this line

/dev/sda5            /mnt/shared  	  vfat       rw,user,umask=000     0 0

I can't see a problem manually changing your fstab entry to something similar (with your own mountpoint and partition info), and then just do a sudo mount -a

---

### Post by bailout on 2007-10-30
> **kosmic said:**
> Why the hell you have this maks = fmask=0111 ?? It will make your drive only Read and execute..

It was simply the line that seemed to work best after trying numerous suggestions from forum posts and various guides. I don't have a clue what the arguments actually do.

---

### Post by bailout on 2007-10-30
Thanks Steve, Does the first line have the brackets in fstab? Your second line is, I think, similar to one I tried previously. I know I tried numerous variations with varying degrees of success. Two programs I use, digikam and amarok, both caused problems in the past, reporting that they didn't have write access to the drive when I could copy files there manually. 

It has always seemed a nightmare just to get full read/write access to the drive and all the files on it.

---

### Post by Steve1961 on 2007-10-30
> **bailout said:**
> Thanks Steve, Does the first line have the brackets in fstab? Your second line is, I think, similar to one I tried previously. I know I tried numerous variations with varying degrees of success. Two programs I use, digikam and amarok, both caused problems in the past, reporting that they didn't have write access to the drive when I could copy files there manually. 

It has always seemed a nightmare just to get full read/write access to the drive and all the files on it.

Hi

Ignore the first line as that was the output of the mount command rather than an fstab line.  Just use

/dev/sda5 /mnt/shared vfat rw,user,umask=000 0 0

but alter the /dev/??? and the mount point to suit your own system.  This line will automount the partition at startup and allow rw access.

This line would also work:

/dev/sda5 /mnt/shared vfat iocharset=utf8,umask=000 0 0

---

