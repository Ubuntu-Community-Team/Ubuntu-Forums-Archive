---
title: "What file system for USB disk????"
date: 2008-04-21
forum: General Help
---

### Post by rado3105 on 2008-04-21
What file system do you recommend to use in USB disk, I ve just bought 1 TB disk WD-RE2GP, when I formatted it using ext3 total capacity was920GB, free space 870GB. When I formated it to reiserfs it had capacity of 930GB(also the free space was 930GB), but it was problem to automount it(i setted it up in /etc/fstab like this:    /dev/sda1   /media/WD1TB   reiserfs defaults   0   0). 
Can you help or give advice what to do? What filesystem to use, or how to change fstab to be automountable??

---

### Post by ibutho on 2008-04-21
Any of the two should be ok to use. What was the exact problem when you used reiserfs? ext3 sets aside some space for the root user in case the disk gets full which could explain the descrepancy in free space (by default 5% is reserved, but I'm sure this can be changed).

---

### Post by rado3105 on 2008-04-21
I couldnt automount it using this in /etc/fstab:  /dev/sda1 /media/WD1TB reiserfs defaults 0 0
I had to mount it mannualy after system loaded, and i don´t want to mount it manually, i want from ti to be automounted(how i dont know).
The next problem was how to set it in fstba to check reiserfs filesystem using reisefsprogs?

---

### Post by ibutho on 2008-04-21
Try
```
/dev/sda1 /media/WD1TB reiserfs defaults 0 1
```

---

### Post by bodhi.zazen on 2008-04-22
Try :

```
/dev/sda1 /media/WD1TB reiserfs auto,users 0 2
```

You may want to change /dev/sda1 to LABEL=xxx or UUID=xxx.yyy.zzz as the device may change depending on other removable media (see the link on fstab below).

The last digit in fstab has to do with checking the file system at boot.
0 = do not check
1 = check first, this is used for /
2 = check after root (there is no 3,4,5, ...)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by dcstar on 2008-04-23
> **bodhi.zazen said:**
> 
........
The last digit in fstab has to do with checking the file system at boot.
0 = do not check
1 = check first, this is used for /
2 = check after root (there is no 3,4,5, ...)


AFAIK this is for **fsck** to check filesystems, not any other tool.

If fsck cannot support a particular filesystem, then I don't believe that you can set these to be checked at boot up.

---

### Post by danwood76 on 2008-04-23
I think whats happening is the USB is being initialised after the fstab has been read so it wont mount your USB disk.

You could add a line to /etc/rc.local like this:
```

mount /media/WD1TB

```
That will mount the drive once everything else in your system has loaded and will save you doing it manually.

Stuff in the fstab doesnt automount once the system has started up.
You could change the disk label to WD1TB and remove the line from fstab and HAL should mount it to /media/WD1TB for you.

---

