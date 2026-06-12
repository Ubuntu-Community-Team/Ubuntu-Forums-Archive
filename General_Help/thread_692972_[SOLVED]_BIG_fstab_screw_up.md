---
title: "[SOLVED] BIG fstab screw up"
date: 2008-02-10
forum: General Help
---

### Post by duckytn on 2008-02-10
Help!

Here is the setup. Running Gutsy with an encrypted file system set up using the alternate install CD. Was "playing" with my fstab file and apparently caused it some harm. Now my system locks up while loading with an error regarding the loading of the X server. I have no command prompt available and not sure how to get to one. The only key combination that works is CTRL-ALT-DEL to reboot the system. I can not use a Live CD as it will not recognize the encrypted partition and/or prompt for the password. 

When I boot now I get the prompt for the password and ubuntu starts to load then crashes with the error.

Any suggestions would be very appreciated!!

Thanks a million!

Eric

---

### Post by taurus on 2008-02-10
Can you at least boot into recovery mode from GRUB menu?  Maybe you can fix your /etc/fstab from there.

---

### Post by duckytn on 2008-02-10
> **taurus said:**
> Can you at least boot into recovery mode from GRUB menu?  Maybe you can fix your /etc/fstab from there.

Thanks for the quick reply!

There right now. It would seem the filesystem is set to readonly and I am trying to figure out how to change that. 

I tried a chmod but it seemed to have no effect. ](*,)

---

### Post by taurus on 2008-02-10
You mean you can't edit /etc/fstab?  What's the output of this command then?

```
ls -la /etc/fstab
```

---

### Post by duckytn on 2008-02-10
The reply is: 

```
-rw-r--r-- 1 root root 630 2008-02-10 10:52 fstab
```

---

### Post by taurus on 2008-02-10
> **duckytn said:**
> The reply is: 

```
-**[COLOR="Blue"]rw[/COLOR]**-r--r-- 1 root root 630 2008-02-10 10:52 fstab
```

Then what do you mean you don't have write permission to it?

```
nano -Bw /etc/fstab
```
When you are done editing, save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by duckytn on 2008-02-10
> **taurus said:**
> Then what do you mean you don't have write permission to it?

```
nano -Bw /etc/fstab
```
When you are done editing, save it with <Ctrl>o and exit with <Ctrl>x.

I get the following error when I hit the <Ctrl>o:

```
Error writing fstab: Read-only file system
```

---

### Post by taurus on 2008-02-10
Are you in the recovery mode, right?  Post the content of your /etc/fstab.

```
cat /etc/fstab
```

---

### Post by duckytn on 2008-02-10
[QUOTE=taurus;4305731]Are you in the recovery mode, right?  Post the content of your /etc/fstab.

Correct. I used the recovery option in the GRUB loader. Here is my fstab file:

```

# /etc/fstab: static file system information.
#
#<file system> <mount point>       <type>   <options>         <dump>   <pass>
proc                   /proc                        proc        defaults             0                0
# /dev/mapper/Workgroup-root
UUID=c1e1b614-cf9f-457f-99d5-0ec053ffd36b    /                       ext3      defaults,data=writeback,errors=remount-ro   0            1
# /dev/sda1
UUID=ae773e2f-87b9-4a34-b0ef-f5af23c9e73c   /boot                ext3        defaults   0         2
# /dev/mapper/Workgroup-swap_1
UUID=930bcc94-93b9-4dda-ad5b-70059f963fa3  none                swap       sw            0         0
/dev/hda             /media/cdrom0      udf,iso9660 user,noauto,exec              0          0




```

---

### Post by duckytn on 2008-02-10
After a bit of searching I found a solution to the problem. Due to the combination of a corrupted fstab and an encrypted filesystem I had to use the steps at the following website to boot off of the Live CD and mount the encrypted filesystem so I could edit the fstab file. 
[URL="http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html"]
http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html[/URL]

Thanks for all the help!

P.S. Google indicated that similar information is available here but the forums were DOA at the time.

---

