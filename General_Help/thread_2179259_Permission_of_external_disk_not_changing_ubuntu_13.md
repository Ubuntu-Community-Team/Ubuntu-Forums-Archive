---
title: "Permission of external disk not changing ubuntu 13.04"
date: 2013-10-07
forum: General Help
---

### Post by zerocool2 on 2013-10-07
i have installed ubuntu 13.04 in my laptop Lenovo G580.

i installed it in a separate partition (not inside window).

i have 4 partitions of 500 GB hard disk,,,,,

problem is that the permission of other partition is not changing , i have tried almost everything (according to my knowledge) but permission remain same as it was before.

please resolve this issue .

---

### Post by arubislander on 2013-10-07
Hi,

You say the permissions of the other partitions are not changing, even though you've tried a few things. 
What have you already tried?
How are the other partitions formatted? FAT32, NTFS, EXT4?
How are the other partitions mounted? Manually, via /etc/fstab?

---

### Post by zerocool2 on 2013-10-07
other partition are NTFS.

all partition are automatically mounted when i start ubuntu, but some time i have to use command for mounting  like this [sudo ntfsfix /dev/sda5].

---

### Post by mcduck on 2013-10-07
NTFS doesn't use simialr system for permissions as Linux uses, so it's not able to handle or store the permissions. Instead the ownership and permissions are set for the whole drive at the time it's mounted, as configured in /etc/fstab file. Trying to sue commands lie chown or chmod will have no effect on NTFS filesystems.

Same applies to FAT as well.

---

### Post by Habitual on 2013-10-07
The technique is discussed in [http://ubuntuforums.org/showthread.php?t=2072007](http://ubuntuforums.org/showthread.php?t=2072007)

but basically goes like this:
Terminal >
```
sudo blkid sda5 
```
in your case.

Now depending on where you want it mounted,
```
sudo mkdir /media/description
```

get your uid and gid with 
Terminal >
```
id
```

then in terminal as root:
```
cp /etc/fstab /etc/fstab.original
vi /etc/fstab
```
and add 

```
UUID=(long string from blkid output) /media/description ntfs-3g rw,uid=1000,gid=100,dmask=022,fmask=133 0 0
```

Change /media/description to something you fancy.
change uid and gid to values from id output
leave the rest of the line as is.

Save and exit editing of /etc/fstab and as root type in terminal>
```
mount -a
```

exit terminal and open another one and type
```
touch /media/description/testfile
mkdir /media/description/testdir
```

Now verify using terminal >
```
ls -al /media/description/testfile
ls -ld /media/description/testdir

```

you should see something akin to this:
[COLOR=#ff0000]-rw-r--r-- [/COLOR]1 jj users 0 Oct 07 2013  8:25 PM /media/Keepers/testfile ([COLOR=#ff0000]644[/COLOR] is correct)
[COLOR=#ff0000]drwxr-xr-x[/COLOR] 2 jj users 4096 Oct 07 2013  8:25 PM /media/Keepers/testdir ([COLOR=#ff0000]755[/COLOR] is correct)

I am not certain, but the ntfs-3g module should be available in most modern kernels, including Ubuntu's.

There may be some issue with where Ubuntu "likes" to mount it, I don't use Ubuntu, so consult the documentation for your release at [https://help.ubuntu.com/](https://help.ubuntu.com/)
or use the man pages present on your system. 
```
man fstab
man mount
man ntfs-3g
```

---

