---
title: "Unionfs/aufs as root fs"
date: 2008-05-08
forum: General Help
---

### Post by deadtrout on 2008-05-08
Hello,
I'm hoping someone has done this before and can help me with some details or point me to a good guide.  I am trying to make the root filesystem on my laptop a unionfs (or aufs) filesystem consisting of 2 partitions on the internal sata drive.
   #1 read-only FS 
   #2 read-write FS

I have searched around (admittedly, not spending more than a couple hours) and find variants of this such as mounting an NFS volume plus a disk partition or a live-cd squashfs + disk partition but nothing directly relating to two partitions of the same drive.  This seems like an important difference and requires a different pivot_root or "mount --move" sequence. Ultimately, I believe I could find *a* way to get this working but I'd like to be confident that I'm doing this in the most robust way.  

Problem: 
I use my laptop both as my main computer at work and as my main computer at home.  Sometimes late at night I've been to casual about installing software and have ended up with a messed up Xorg.  You can imagine how unhappy my boss is when I spend the first hour unf***ing my laptop.

Idea:
I would like to have a system where I can delete all of last nights changes and move forward with a known solid system.  If I make some changes to the system and want to commit them I can simply merge the r/w partiton into the r/o partion.  

This also means I can tinker with the system knowing I may do something horribly wrong but be sure I can undo it all very quickly.

I'm not sure whether I should be investigating unionfs or aufs or possibly some other variant.  I also am not clear on where in the initrd/init sequence is best to remount everything in the way I describe.  

If anyone has any pointers or information I'd be happy to spend a few evenings trying it all out and writing it up in a howto.

Thanks,
-Terry

---

### Post by BlaY0 on 2008-07-20
OK, here I made a script inspired by Nicholas A. Schembri that  does just what you expected. I use this script to make a union of my squashfs root partition and tmpfs. First it mounts root partition read-only and then any other partition that you would like to use as a read-write in union with root partition:

```

#!/bin/sh -e

case $1 in
  prereqs)
    exit 0
    ;;
esac

for x in $(cat /proc/cmdline); do
  case $x in
    root=*)
      ROOTNAME=${x#root=}
      ;;
    aufs=*)
      UNION=${x#aufs=}
        case $UNION in
          LABEL=*)
            UNION="/dev/disk/by-label/${UNION#LABEL=}"
            ;;
          UUID=*)
            UNION="/dev/disk/by-uuid/${UNION#UUID=}"
            ;;
        esac    
      ;;
  esac
done

if [ -z "$UNION" ]; then
    exit 0
fi

modprobe -Qb aufs

# make the mount points on the init root file system
mkdir /aufs /ro /rw

# mount read-write file system
if [ "$UNION" = "tmpfs" ]; then
  mount -t tmpfs rw /rw -o noatime,mode=0755
else
  mount $UNION /rw -o noatime
fi

# move real root out of the way
mount --move ${rootmnt} /ro

mount -t aufs aufs /aufs -o noatime,dirs=/rw:/ro=ro

# test for mount points on union file system
[ -d /aufs/ro ] || mkdir /aufs/ro
[ -d /aufs/rw ] || mkdir /aufs/rw

mount --move /ro /aufs/ro
mount --move /rw /aufs/rw

# strip fstab off of root partition
grep -v $ROOTNAME /aufs/ro/etc/fstab > /aufs/etc/fstab

mount --move /aufs /root

exit 0

```

1. Put this script into [FONT="monospace"]/etc/initramfs-tools/scripts/init-bottom/[/FONT], make it executable.

2. Put [FONT="monospace"]aufs[/FONT] into [FONT="monospace"]/etc/initramfs-tools/scripts/modules[/FONT] so [FONT="monospace"]aufs[/FONT] module will be added to initramfs image later on.

3. Reconstruct initramfs image with [FONT="monospace"]update-initramfs -u[/FONT].

4. Add [FONT="monospace"]aufs=<your_union_rw_partition>[/FONT] to your boot loader's kernel parameters. If you would like to use RAM as your read-write store put there [FONT="monospace"]aufs=tmpfs[/FONT].

---

### Post by dementic on 2009-06-13
The method doesn't works for me, I copied the script, then put it in the specified directory. Then added aufs in /etc/initramfs-tools/modules, saved. Reconstructed and then added aufs=tmpfs in grub. But it still writes files to the hard disk. Did I something wrong??

I use Ubuntu 9.04

---

### Post by salsasepp on 2009-07-14
I used the above script as described, works for me. Nice!

Question: Now I would like to do a persistent software update. I need to remove the /rw branch from the union and remount /ro in rw mode. 

My naive line
  mount -t unionfs -o remount,del=/rw none /
results in
  [FONT=Courier New]mount: / is busy.[/FONT]

How would I do this correctly?

Thank you,
  Stefan.

---

### Post by damiannz on 2012-03-01
ok i just got this working with my pandaboard running ubuntu 10.10 (omap4). 2 tweaks:

1. ```
/etc/initramfs-tools/scripts/modules
``` should be ```
/etc/initramfs-tools/modules
```
2. remove ```
modprobe -Qb aufs
``` as aufs is builtin and this line causes the script to bail out. 

console output: using ```
printf "blah blah blah"
``` was very useful for debugging. it's unclear though if one can also ```
echo
``` in initramfs-scripts.

---

### Post by oldos2er on 2012-03-01
Closed, necromancy.

---

