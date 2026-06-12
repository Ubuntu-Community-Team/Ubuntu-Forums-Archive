---
title: "Fsck does not seem to run automatically"
date: 2013-05-03
forum: General Help
---

### Post by SuperFreak on 2013-05-03
I am not sure if this is due to my fstab configuration but I have not seen fsck run automatically on my computer and I have had it for over a year (I turn off the computer every night). 

```
david@MainSqueeze:~$ showfsck
Unable to access information for /dev/disk/by-uuid/fb91ba53-76d5-41af-aa6f-24035b6de7a4
Unable to access information for /dev/sda4
Unable to access information for /dev/sdb1
Unable to access information for /dev/sdb2
david@MainSqueeze:~$ 


```
How do I enable fsck?

---

### Post by oldos2er on 2013-05-03
I believe you need to run showfsck as root, thus ```
sudo showfsck
```

---

### Post by Dennis N on 2013-05-03
Automatic file system checking has been disabled on the isos of the past two releases (12.10, 13.04) of Lubuntu and Xubuntu, at least for the i386 versions. I don't know about Ubuntu. 

To check, run the following but replace sda7 by the appropriate partition:

```
dn@Alexa:~$ sudo dumpe2fs -h /dev/sda7 | grep "mount count" 
dumpe2fs 1.42.5 (29-Jul-2012) 
Maximum mount count:      -1

```

If the Maximum mount count = -1 as above, the checking is disabled.

Fix: to set file system checking every 40 boots:

```
dn@Alexa:~$ sudo tune2fs -c 40 /dev/sda7 
tune2fs 1.42.5 (29-Jul-2012) 
Setting maximal mount count to 40

```

(All code above is actual output from Lubuntu 13.04 after installation.)

---

### Post by Dennis N on 2013-05-03
Just checked my past installation notes, and the automatic checking was also disabled when I installed **Xubuntu 12.04**, so the situation goes back that far.

---

### Post by SuperFreak on 2013-05-03
@oldos2er - Thanks, it appears fsck is not enabled on any of my ext4 drive partitions

@Dennis N - Thanks I have enabled fsck to run every 30 times using your instructions. Much appreciated


I wonder why fsck had been disabled. I run Ubuntu

---

### Post by Dennis N on 2013-05-03
As a related issue, if you run showfsck with maximum mount count = -1 (fsck disabled), over time you will get (increasingly) negative numbers as the number of mounts remaining. This thread dealt with that and why it happens:

[http://ubuntuforums.org/showthread.php?t=2089230](http://ubuntuforums.org/showthread.php?t=2089230)

Ideally, showfsck should be modified to report that fsck is disabled if that is the case.

---

