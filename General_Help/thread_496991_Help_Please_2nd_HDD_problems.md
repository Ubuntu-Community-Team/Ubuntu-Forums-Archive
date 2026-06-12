---
title: "Help Please 2nd HDD problems"
date: 2007-07-09
forum: General Help
---

### Post by anubistheonetrue on 2007-07-09
I Have been working on this with the info already posted but must have not got it right....
i want to give permission my main desktop but as more storage but i have failed.
it is the 160 GB drive.
here is the fdisk command:

baal@bal-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       29834   239641573+  83  Linux
/dev/hdb2           29835       30401     4554427+   5  Extended
/dev/hdb5           29835       30401     4554396   82  Linux swap / Solaris

Disk /dev/sda: 203.9 GB, 203928109056 bytes
16 heads, 63 sectors/track, 395136 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      395136   199148512+   7  HPFS/NTFS
baal@bal-desktop:~$

---

### Post by Turboaaa2001 on 2007-07-09
Please explain more clearly. Is the 160GB (hda) drive the one with your OS? If so then are you trying to add the other drives?

---

### Post by marsbt on 2007-07-09
Yup, please explain what you are trying to do?

---

### Post by anubistheonetrue on 2007-07-09
the 250GB has the OS
the 160GB is empty
thx

---

### Post by anubistheonetrue on 2007-07-09
yes my 250 GB is almost full and i cant write to my 160GB drive because i have set i up incorrectly. every time i boot now it stops because it is configured wrong. and i have to hit ctrl d to finish the boot.

I just want to be able to read and write to both drives from the desktop.

any help?

---

### Post by confused57 on 2007-07-09
> **anubistheonetrue said:**
> yes my 250 GB is almost full and i cant write to my 160GB drive because i have set i up incorrectly. every time i boot now it stops because it is configured wrong. and i have to hit ctrl d to finish the boot.

I just want to be able to read and write to both drives from the desktop.

any help?

This should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
or
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

---

### Post by Nythain on 2007-07-09
give this a whirl... create a directory
```

mkdir ~/Desktop/storage

```then open up your /etc/fstab
```

gksudo gedit /etc/fstab

```and add a line like this
```

/dev/hda1    /home/yourusername/Desktop/storage   ext3    defaults    0  2

```making sure yourusername is the name you log in with, and changing ext3 to ext2 if you used that for some reason instead of ext3
then in terminal type
```

sudo mount -a

```now your storage drive should automount at ~/Desktop/storage everytime you boot, and you should be able to read/write to it (hopefully, if not you will have to sudo chown 1000:1000 ~/Desktop/storage so that you own it, then you should get read write onto it)


edit: took me to long to post, and you actually posted your problem more accurately, not sure if any of this is going to help you actually... where is your /dev/hda1 being mounted to at the moment???

---

### Post by anubistheonetrue on 2007-07-10
thanks so much guys got it working!!

---

### Post by ~/Chromekaldra/~ on 2008-01-14
> **Nythain said:**
> give this a whirl... create a directory
```

mkdir ~/Desktop/storage

```then open up your /etc/fstab
```

gksudo gedit /etc/fstab

```and add a line like this
```

/dev/hda1    /home/yourusername/Desktop/storage   ext3    defaults    0  2

```making sure yourusername is the name you log in with, and changing ext3 to ext2 if you used that for some reason instead of ext3
then in terminal type
```

sudo mount -a

```now your storage drive should automount at ~/Desktop/storage everytime you boot, and you should be able to read/write to it (hopefully, if not you will have to sudo chown 1000:1000 ~/Desktop/storage so that you own it, then you should get read write onto it)


edit: took me to long to post, and you actually posted your problem more accurately, not sure if any of this is going to help you actually... where is your /dev/hda1 being mounted to at the moment???

I got this:

```
mount: special device /dev/hda1 does not exist
``` 

but i followed your directions to a tee

*EDIT*

nevermind, a tut got me through it all, but if i have your attention, i suppose i could ask a small extension question: How do i add this 'storage' folder to my Places? That way it's not on my desktop? Like, iknow if i drag it to my side bar (it's on my right for me) i get a little short cut icon, but it'll still be on my desktop so....

Oh, also, If i want to move my VM to the new Hdd, can i do that?

---

