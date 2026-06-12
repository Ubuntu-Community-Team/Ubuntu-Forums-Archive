---
title: "old samba shared directory on a new installation"
date: 2019-08-14
forum: General Help
---

### Post by adriano49 on 2019-08-14
Hi everybody,
I had an ubuntu server that didn't work anymore.
So I took the phisical hard disk (2Terabytes) where i made my backups from windows machines through samba and mounted it on a new machine, where i installed ubuntu 18.04.3
Now, i can see the disk on the files system by the ubuntu GUI, and i see that it is half used. That's reasonable, according to the dimension of my backupped files during several years.
But, i can't see/find the files! 
How can i reach them?
Please help, on that hard disk i have unic copies.
Thanks in advance.

---

### Post by TheFu on 2019-08-15
If the files are pure data used by 1 userid, then whatever you did to copy them is probably fine.  

But, if the files are a full Linux backup, then you've lost 50% of the data required for a system restore to work.  The permissions, owner, group and ACLs are needed for Unix programs, system settings and system data to be useful without 500,000 manual operations to put the permissions back.

Ok, so let's assume it is first and the disk is using the ext4 file system. Please verify the file system first, because it matters.
GUIs tend to use pseudo-file mounting techniques which aren't the same a "real mounts".  There are 3 ways to get a "real mount", IMHO.

[LIST]
[*]/etc/fstab config file - good for permanently connected storage.
[*]manually running **mount** command
[*]autofs - good for USB or network storage that is not always connected. This is more complex than the other options, but can be very handy.
[/LIST]

After you have a real mount, the **df -hT** command will show the file system used:
```
$ dft
Filesystem                      Type  Size  Used Avail Use%   Mounted on
/dev/mapper/ubuntu--vg-root     **ext4**   25G   11G   13G  47% /
/dev/mapper/ubuntu--vg-home--lv **ext4**   74G   21G   51G  29% /home
/dev/sda2                       **ext2**  721M  146M  538M  22% /boot
/dev/mapper/ubuntu--vg-stuff    **ext4**   99G  1.5G   92G   2% /stuff
/dev/sda1                       **vfat**  511M  3.7M  508M   1% /boot/efi

```
Here is an example fstab entry for one of my file system mounts:
```
# <file system>              <mount point>   <type>  <options>                  <dump>  <pass>
/dev/mapper/ubuntu--vg-home--lv     /home	ext4       errors=remount-ro,noatime      0   2
```

There's a tutorial on setting up the fstab. "ubuntu fstab" is the search.
There's a tutorial on setting up autofs. "ubuntu autofs" is the search.
Once we see relevant output for this other disk, we can provide the **mount** command and with a little more data, the fstab configuration line.

When posting commands and outputs here, please, please, use *code tags* as I've done above - that's AdvEdit with (#).  If it doesn't look just like the output in the terminal, please fix it.

---

