---
title: "sudo chmod does not change permissions"
date: 2014-05-25
forum: General Help
---

### Post by Apagon on 2014-05-25
Hi Folks, 

I insert a usb key; it does not mount auto; 
I sudo blkid and mount it as: 
sudo mount /dev/sdb1 /media

there, we have: 
drwxr-xr-x  2 root root 4.0K Jan  1  1970 .
drwxr-xr-x 21 root root 4.0K May 11 17:54 ..
-rwxr-xr-x  1 root root 627K May 22 22:02 <filename1.txt>
-rwxr-xr-x  1 root root 2.1M May 22 22:50 <filename2.txt>
-rwxr-xr-x  1 root root  100 May 23 13:21 <filename3.pdf>
-rwxr-xr-x  1 root root 180K May 23 14:12 <filename4...>
-rwxr-xr-x  1 root root    0 May 24 13:53 <filename5...>

I want to give full permission to the dir /media and all files inside it:
sudo chmod -R 777 /media 
the command is accepted but the result is null; the permissions are still the same. 

I try (beeing pretty it wont change anything anyway): 
sudo find /media -type d -exec chmod 777 {} \;
sudo find /media -type f -exec chmod 777 {} \;

both commands are accepted (no output errors), but the permissions remain the same. I try 700 instead of 777, no error in the output but the permissions still havent changed (still have r_xr_x)

so I (desesperatly) mkdir: /media/bruce/usb: 
drwxr-xr-x 2 doyle doyle 4096 May 24 14:40 /media/doyle/usb/
(as you noticed, mount point is not root/root anymore)
I mount my usb key in it. 
The problem remains. 

any suggestion is welcome!

---

### Post by whitesmith on 2014-05-25
How is your usb key formatted? Win formats (ntfs, etc.) don't recognize *nix permissions, so you could try forever and not be able to change anything, even if mount point is changed. Regards.

---

### Post by mcduck on 2014-05-25
Like whitesmith said, filesystesms such as FAT and NFTS lack support for Unix-style ownershps and permissions so you can use commands like chown and chmod to set them for individual files or directories.

Instead, the permissions are set for the whole filesystem at the time it's mounted. Try something like this:

```
sudo mount /dev/sdb1 /media/usbdrive -o rw, uid=1000,gid=1000,umask=000,dmask=000
```

---

### Post by whitesmith on 2014-05-25
> **mcduck said:**
> Like whitesmith said, filesystesms such as FAT and NFTS lack support for Unix-style ownershps and permissions so you can use commands like chown and chmod to set them for individual files or directories.

Instead, the permissions are set for the whole filesystem at the time it's mounted.In the interest of clarity I believe you meant to say: "[F]ilesystesms such as FAT and NFTS lack support for Unix-style ownershps and permissions so you can **not** use commands like chown and chmod to set them for individual files or directories." Your mount comment seems right, even thought I never had occasion to use it. (My stuff is 100% Linux.) Regards.

---

### Post by Apagon on 2014-05-25
thanx for your suggestions. 

mount
[...]
/dev/sdb1 on /media/bruce/usb type vfat (rw)
/dev/sdd1 on /media/bruce/FX type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=
udisks2)

sdb1 is the faulty one.
sdd1 works fine. I can edit write save txt files.
both have vfat. 

now, the fs on this usb stick may be corrupted because when I try to mount it on another computer: 
sudo mount /dev/sdb1 /mnt 
got the following: 
mount: wront fs type, bad option, bad superblock on /dev/sdb1,
    missing codepage or helper program, or other error 
    In some case useful info is found insyslog - try 
    dmesg | tail or so 

tried to look in dmesg and syslog but nothing found. 

anyway I will format and try again. 
Thank you very much again.

---

### Post by whitesmith on 2014-05-25
You're welcome. Please use Thread Tools at top right of the page to close this thread if it is solved to your satisfaction. Cheers.

---

