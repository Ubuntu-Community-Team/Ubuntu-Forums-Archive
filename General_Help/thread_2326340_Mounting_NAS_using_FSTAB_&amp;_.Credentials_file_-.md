---
title: "Mounting NAS using FSTAB &amp; .Credentials file - works on Linux Mint, not on Ubuntu"
date: 2016-05-30
forum: General Help
---

### Post by scott.bouch on 2016-05-30
Hi all,

Just looking to see if there is something fundamental that differs between Linux Mint and Ubuntu.

On my Mint machine I use FSTAB and a .credentials file in /root to mount my NAS, called nas2.

I wanted to achieve the same on my Ubuntu 14.04 machine, so I copied the line into fstab:
```
//192.168.1.76/nas2 /mnt/nas2 cifs credentials=/root/.nas2cred,rw,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777
```

And I copied the .credentials file to the same folder as the Mint machine /root.

When I use** sudo mount -a**, I get this:

```
$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //192.168.1.76/nas2,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


I thought it may be a permissions issue, so I followed this guide here: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) and did:
```
$ sudo chmod 600 .nas2cred
```

But alas, the same issue persists.

I can browse the network using Nautilus and add bookmarks, but for certain programs I really need it permanently mounted in my /mnt directory.

I got it working on the Mint machine with the above entries more by luck than judgement, so by no means fully understand about users and permissions etc.. (ie: I may need a little hand-holding!)

Thanks, Scott.

---

### Post by CharlesA on 2016-05-30
Have you looked here?

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by Morbius1 on 2016-05-31
Every now and then Linux throws you an error message that despite their best efforts to do the opposite actually gives you a hint as to what the problem is like this one:
> (for several filesystems (e.g. nfs, cifs) you might        need a /sbin/mount.<type> helper program)
The "helper program" is likely cifs-utils. Install it and see if the error message goes away - or at least gives you a different error message:
```
sudo apt-get install cifs-utils
```

---

