---
title: "can't access windows partition"
date: 2012-10-24
forum: General Help
---

### Post by llogg on 2012-10-24
I am having a similar issue to the OP.  I just installed Ubuntu 12.10 as a dual boot with Windows Vista Home Basic.  Wubi automatically installed the 64 bit Ubuntu though my Vista install was 32 bit.  Now I can't seem to find the Windows files in Nautilus.

Following the instructions [here]("https://help.ubuntu.com/community/MountingWindowsPartitions") I ran the NTFS-config utility.  I was not asked to provide a name.  I then rebooted and ran ```
sudo mount -a
```  I still couldn't see the Windows files in Nautilus so I opened the Disk Utility and see what I think is the Windows partition as /dev/sda1, shown as "In use, mounted at /host".  How do I access these files?  The main issue is I want to set up my media library without copying all those files over to the new partition.  Thanks.

---

### Post by Tralce on 2012-10-24
In Nautilus, click on File System, then browse to "host".

---

### Post by coffeecat on 2012-10-24
@llog, Ive moved your post from the thread you posted to because yours is a different issue - you have a wubi install. So your first question is easily answered. Open a Nautilus file browser and look for File System in the left pane. Click on that and then open the host folder in the main pane. That is your Windows host partition file system. If you installed wubi to the C: partition, that is the C: partition.

And now to ntfs-config. This is an unmaintained and obsolete piece of software which you do not need for mounting the Windows partition, and if you have any other NTFS partitions, you are probably better mounting them from Nautilus anyway. Please uninstall ntfs-config. Also, please post the output of this terminal command:

```
cat /etc/fstab
```

So that we can see if ntfs-config has made unnecessary additions to that file. If it has, I can show you how to remove them.

As far as ntfs-config being recommended on an Ubuntu wiki, I'm really lost for words. I sincerely hope that is simply an oversight from when ntfs-config was a recommended way of doing things. I'll look into that and consult with others concerning an edit to that page. Thanks for drawing attention to it.

---

### Post by llogg on 2012-10-25
Thanks for the help.  I feel silly that I didn't see the host folder in Nautilus.  So that issue is solved.  Here's the output of ```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/sda1    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    00
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0

```

---

### Post by coffeecat on 2012-10-26
> **llogg said:**
> 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/sda1    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    00
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0

```


@llogg, I'll get someone who knows more about wubi installs to have a look at this. I'm not sure about the /dev/sda1 line. For one thing, there should be a space between the 0's at the end of the line. Did you have any problem copying and pasting this output?

---

### Post by bcbc on 2012-10-26
You can delete the /dev/sda1 entry. While it doesn't seem to be causing problems, it's not doing anything useful either.

Just a note on the /etc/fstab for Wubi installs. Since Wubi started using preinstalled disk images by default for Ubuntu, the /etc/fstab has been missing an entry for / (root). You still see it if you install with the ISO or if you install any of the other flavours (Kubuntu, Lubuntu etc.). But it is apparently not needed - the process of mounting the /host and loop mounting the root.disk is taken care of prior to processing the /etc/fstab

So... this would be normal for a diskimage:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
```But this is also normal (ISO installs via ubiquity):```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```So either of those seems to be fine.

PS here's my bug report from when they introduced the diskimage installs. At that time both the / and swap entries were missing. They fixed the swap, but didn't add /: [https://bugs.launchpad.net/bugs/857954](https://bugs.launchpad.net/bugs/857954)

---

### Post by bcbc on 2012-10-26
I just checked an ISO install of 12.10 and the /etc/fstab no longer has the proc entry:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```

---

### Post by llogg on 2012-10-27
> **bcbc said:**
> You can delete the /dev/sda1 entry. While it doesn't seem to be causing problems, it's not doing anything useful either.

Just a note on the /etc/fstab for Wubi installs. Since Wubi started using preinstalled disk images by default for Ubuntu, the /etc/fstab has been missing an entry for / (root). You still see it if you install with the ISO or if you install any of the other flavours (Kubuntu, Lubuntu etc.). But it is apparently not needed - the process of mounting the /host and loop mounting the root.disk is taken care of prior to processing the /etc/fstab

So... this would be normal for a diskimage:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
```But this is also normal (ISO installs via ubiquity):```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```So either of those seems to be fine.

PS here's my bug report from when they introduced the diskimage installs. At that time both the / and swap entries were missing. They fixed the swap, but didn't add /: [https://bugs.launchpad.net/bugs/857954](https://bugs.launchpad.net/bugs/857954)so do I just do ```
$gksudo gedit /etc/fstab
``` and delete the 
```
/dev/sda1
``` then save, close, and reboot?

---

### Post by bcbc on 2012-10-27
You got it.

Although technically you don't have to reboot since that line doesn't appear to be doing anything. If you add something to /etc/fstab you don't have to reboot either - you can just mount it with:
```
sudo mount -a
```

---

