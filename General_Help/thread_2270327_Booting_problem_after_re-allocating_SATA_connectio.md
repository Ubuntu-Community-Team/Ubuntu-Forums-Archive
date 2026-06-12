---
title: "Booting problem after re-allocating SATA connection"
date: 2015-03-22
forum: General Help
---

### Post by satimis on 2015-03-22
Hi all,

This is an old box (spare) which has not been run for sometimes.  Because of the problem of a defective SATA connector on the motherboard I just re-allocated the HDs connection on SATA connectors

Available SATA connectors on motherboard = 5, one defective

Original setup: dual boot as follows, selected on motherboard BIOS

Hard drives:
1)
WD HD (1.5TB) - Ubuntu 14.04
running Oracle VirtualBox

2)
SSD (120G) - Debian OS
Seagate HD (640G) - for running VMs


Booting 1) Ubuntu 14.04 following warning popup```

error: diskwriter writes are not supported
Press any key to continue

```

ALT+F2 doesn't work

Press "Ent" to continue


Warning```

The disk drive for /medit/ssd is not ready yet or not present
Continue to wait, or Press S to skip mounting or M for manual recovery

```

Press S to boot Ubuntu 14.04

$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/LVM1.5D-root /               ext4    errors=remount-ro 0       1
/dev/mapper/LVM1.5D-data /data           ext4    defaults        0       2
/dev/mapper/LVM1.5D-swap none            swap    sw              0       0

/dev/debian731/root     /media/ssd      ext4    defaults         0 0

```


Unable to boot
2)
SSD - Debian OS
WD HD - for running VMs

Warning```

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press key

```


Please help.  Thanks

Regards
satimis

---

### Post by bardo2 on 2015-03-23
Hi,
usually, i am not shy to look at software/configuration problems. But as soon as hardware is in the mix, i must confess: it is too frustrating, because defects there usually cannot be worked on through commands. (Like: what is the command line to switch on a computer?) ;-)
And... i do not understand enough of electronic circuits, or SATA protocols for being able to help out. Why do you think, your hardware is ok and plugged in the right way? You know, you can find water in the toilet, but i wouldnt try to make a tee from it. ;-)

---

### Post by Yellow Pasque on 2015-03-24
I thought you had 2 defective SATA ports and you were going to get an add-in card?
[http://ubuntuforums.org/showthread.php?t=2270068](http://ubuntuforums.org/showthread.php?t=2270068)

Just a question - Do you have the latest BIOS installed?

---

