---
title: "trying to create ramdisk"
date: 2012-12-20
forum: General Help
---

### Post by hunterkasy on 2012-12-20
I am trying to create some ramdisk, I am following a post:[http://blog.endpoint.com/2012/04/easy-creating-ramdisk-on-ubuntu.html](http://blog.endpoint.com/2012/04/easy-creating-ramdisk-on-ubuntu.html)

here is what I typed in the terminal:

 sudo mount -t tmpfs -o size=2048M,mode-777 tmpfs /home/tyler/ramdisk

I already created the ramdisk folder in my home dir.

this is what I get after I entered it: 

mount: wrong fs type, bad option, bad superblock on tmpfs,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

How should I do it?

---

### Post by hunterkasy on 2012-12-20
ok I got it figured out how to ramdisk a file, now I would like to know how to make ramdisk drive that shows up just like another hhd

---

### Post by hunterkasy on 2012-12-21
help please

---

### Post by hunterkasy on 2012-12-21
so far this is what I have done:

> mkdir -p /media/ramdisk
mount -t tmpfs -o size=2048M tmpfs /media/ramdisk/


I want it to show up as another drive, but so far it doesn't

---

### Post by rnerwein on 2012-12-22
> **hunterkasy said:**
> so far this is what I have done:



I want it to show up as another drive, but so far it doesn't
hi
where will you see it. you can see it with: mount 
cheers

---

### Post by vanadium on 2012-12-22
If you mount it on a mount point under /media, it will be presented as another drive in nautilus and in the Unity launcher.

---

### Post by hunterkasy on 2012-12-22
> **vanadium said:**
> If you mount it on a mount point under /media, it will be presented as another drive in nautilus and in the Unity launcher.

how do I do that?

---

### Post by hunterkasy on 2012-12-23
help again please

---

### Post by vanadium on 2012-12-23
Sorry, I did not notice that you already mounted it under /media before (/media/rsmdisk). I would expect that then it would be presented as a drive in nautilus and in the Unity launcher. Is it mounted correctly after all? Does it show up in the output of "mount" after you have mounted it?

---

### Post by StinkySQL on 2012-12-23
> **hunterkasy said:**
> so far this is what I have done:



I want it to show up as another drive, but so far it doesn't



Did you try the -L label option for the mount command? Is that what you are looking for?

---

### Post by StinkySQL on 2012-12-23
Also note that the directory you created is not the same spelling as the mount command is using.

---

### Post by hunterkasy on 2012-12-23
> **StinkySQL said:**
> Also note that the directory you created is not the same spelling as the mount command is using.

thanks for pointing that out, that was just a misspell when typing it in here,

when I type df -h | grep media I get this:

tyler@tyler-main:~$ df -h | grep media
tmpfs                   2.0G     0  2.0G   0% /media/ramdisk

---

### Post by vanadium on 2012-12-24
I have tried it myself, but indeed, no volume icon is presented. With physical disks, the behaviour has always been that an icon is automatically presented for drives mounted under /media. I guess you will need to create lauchers yourself, or work with symlinks, for convenient access to the drive.

---

### Post by hunterkasy on 2012-12-25
> **vanadium said:**
> I have tried it myself, but indeed, no volume icon is presented. With physical disks, the behaviour has always been that an icon is automatically presented for drives mounted under /media. I guess you will need to create lauchers yourself, or work with symlinks, for convenient access to the drive.

thanks for all your help,  I don't know how to do any of that without help

---

### Post by StinkySQL on 2012-12-25
Starting to get the feeling you cannot get that Icon. Check out this discussion.
[http://ubuntuforums.org/showthread.php?t=1687103](http://ubuntuforums.org/showthread.php?t=1687103)

SS

---

