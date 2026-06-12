---
title: "Encrypted /home eating up space"
date: 2020-02-02
forum: General Help
---

### Post by nycjeff on 2020-02-02
So my /home only has  about 6GB of stuff in it, but it seems like the encrypted directory /.encryptfs has at least 64gb, which doesn&#8217;t seem right.
I keep getting these warning messages saying that I was running out of space, so I&#8217;m deleting old kernels, clearing caches, clearing out unused programs, but it keeps getting worse and seems to be related to the encrypted /home that I set up in the original install.
I&#8217;ve found a few forum posts around that talk about this without really finding a good answer. Any suggestions before I try a fresh install?

---

### Post by nycjeff on 2020-02-02
Will probably just end up removing the encryption using the procedure at this link.
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#How_to_Remove_an_Encrypted_Private_Directory_Setup](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How_to_Remove_an_Encrypted_Private_Directory_Setup)
Crossing fingers.

---

### Post by TheFu on 2020-02-02
Manually empty the trash?

This command and output would be helpful:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

BTW, encrypted HOMEs was deprecated ni 16.04, I think. If you want encryption, best to do it at the full LV or Partition level.

---

### Post by nycjeff on 2020-02-03
> **TheFu said:**
> Manually empty the trash?

This command and output would be helpful:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

BTW, encrypted HOMEs was deprecated ni 16.04, I think. If you want encryption, best to do it at the full LV or Partition level.


Thanks for the response. 
yes, have emptied the trash. 

using that command I get the following:
jeff@Toshi:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sda5      ext4      19G   17G  388M  98% /
/dev/sdb2      vfat     256M   55M  202M  22% /boot/efi
/dev/sda1      vfat     509M  3.2M  506M   1% /media/jeff/9C5D-F211
/dev/sda3      ext4     890G   64G  781G   8% /media/jeff/70ab4203-39f2-4468-81c0-fc2d9b2602e2
/dev/sdb4      fuseblk  224G   80G  144G  36% /media/jeff/TI10668100A

---

### Post by TheFu on 2020-02-03
> **nycjeff said:**
> Thanks for the response. 
yes, have emptied the trash. 

using that command I get the following:```

jeff@Toshi:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sda5      ext4      19G   17G  388M  98% /
/dev/sdb2      vfat     256M   55M  202M  22% /boot/efi
/dev/sda1      vfat     509M  3.2M  506M   1% /media/jeff/9C5D-F211
/dev/sda3      ext4     890G   64G  781G   8% /media/jeff/70ab4203-39f2-4468-81c0-fc2d9b2602e2
/dev/sdb4      fuseblk  224G   80G  144G  36% /media/jeff/TI10668100A
```

19G is tiny for a normal Ubuntu desktop, unless you carefully manage storage use.  I do that on my primary desktop:
```
$ dft
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4   20G   15G  3.2G  83% /

```
but most of my storage is available as NFS.  For most people, 25G for / assuming there is a separate /home/ partition.  Partitions under /media/ aren't part of /home/.  If you want, you could make /dev/sda3    /home/.  It isn't hard, but you'll need to edit the fstab manually and move files over from /home/ on /dev/sda5 .

BTW, see how much easier it is to read the df output because I used code tags?  Please learn to do that for all command output.

---

