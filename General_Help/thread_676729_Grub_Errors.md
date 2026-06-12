---
title: "Grub Errors"
date: 2008-01-24
forum: General Help
---

### Post by scott.medling on 2008-01-24
Hey guys, I'm having trouble with grub.  I think it's unable to find my /boot partition.  It often returns error 17 or 21 (unable to find or mount specified partition).

I have 5 hard drives in the system, which are called sd[a-e] in a various orders every time it boots -- 4 are sata, and I can't recall if the last is pata or sata.

I just installed Ubuntu (7.10) and when it didn't boot I put the LiveCD in and ran grub-install onto every hard drive in the system.  The menu.lst file contains the UUIDs so I'm really not sure why there was a problem to start with.  I've tried messing around with menu.lst changing (hd0,0) to (hd1,0) and so on but to no avail.

Any help would be appreciated.  Thanks.

---

### Post by zvacet on 2008-01-24
Where did you installed Ubuntu(wich drive and partition)?You didn´t put in blindly,didn´t you?

---

### Post by scott.medling on 2008-01-24
When installing I partitioned manually (with the GUI installer), using partition 1 of a drive for the /boot, partition 2 for /, and partition 3 for swap, telling it to reformat all of those partitions' filesystems.  At the time I installed Ubuntu, the drive was /dev/sda.  Recently, it's been showing up as /dev/sdd more often.

---

### Post by capink on 2008-01-24
I think you might have a problem with your device.map file. I am not sure whether the following solution is going to work

1. Boot your pc using the live cd.
2. mount your root direcotry under /mnt

```
sudo mount -t ext3 [COLOR="Magenta"]/dev/sdXY[/COLOR] /mnt
```

replace [COLOR="Magenta"]/dev/sdXY[/COLOR] with the value corresponding to your **root** partition.

3. Mount your boot partition under /mnt/boot

```
sudo mount -t ext3 [COLOR="Magenta"]/dev/sdXY[/COLOR] /mnt/boot
```

replace [COLOR="Magenta"]/dev/sdXY[/COLOR] with the value corresponding to your **boot** partition.

4. Chroot into your installation

```
sudo mount -o bind /dev /mnt/dev
```
```
sudo mount -o bind /proc /mnt/proc
```
```
sudo chroot /mnt
```

And perform the following from within chroot.

Delete your old device.map file:

```
rm /boot/grub/device.map
```

Create a new device.map file using the following command:

```
grub --batch --device-map\=/boot/grub/device.map < /dev/null
```

Run the following command: [COLOR="Red"](This command has to be run to overcome a bug)[/COLOR]

```
blkid
```

Rename your old menu.lst file:

```
mv -v /boot/grub/menu.lst{,_bak}
```

Run the command update-grub which will create a new menu.lst file:

```
update-grub
```

If it asks you:

> Would you like /boot/grub/menu.lst generated for you? (y/N) 

Answer yes and press Enter.

Exit chroot

```
exit
```

5. Run the following command to reinstall grub ( make sure your boot and root partitions are still mounted ):

```
sudo grub-install --root-directory=/mnt/boot '(hd0)'
```



Edit: The solution posted above might produce a menu.lst that has no entries for your windows system. You will have to manually copy the entry for windows from your old menu.lst file (/boot/grub/menu.lst_bak)

---

### Post by scott.medling on 2008-01-25
Thanks for the help but it's still not working (grub returns error 21 at the moment).  When running command 5, it reprobed my devices; would this undo running "blkid" to overcome that bug you mentioned?

Also, after I rebooted it mounted the drives in a different order but still thinks in device.map that they should be paired the way they had been.

---

### Post by logos34 on 2008-01-25
> **scott.medling said:**
> The menu.lst file contains the UUIDs so I'm really not sure why there was a problem to start with.

Me neither.  The fact that the sata controller(s) and Bios are playing musical drivenames every boot shouldn't matter--menu.lst and fstab should be able to find them using the UUIDs.

Try this variation:

-Set the ubuntu drive first in the Bios hard disk boot priority.  THEN, from the live cd, reinstall Grub to the mbr of the ubuntu drive using the grub shell.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Your menu.lst root line should point to the separate /boot at (hd**0**,0).  The UUID= on the kernel line should also correspond to /boot (not /).

---

