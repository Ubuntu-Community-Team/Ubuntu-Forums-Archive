---
title: "sda and sdb - I want to switch the hd designations - how?"
date: 2019-12-27
forum: General Help
---

### Post by ra7411 on 2019-12-27
I want to make sdb show up as sda and vice versa.

If it can be done without messing up things it would be from "try ubuntu" while they're unmounted, right?

If it can be done without nuking things, how?

Thanks

---

### Post by CelticWarrior on 2019-12-27
That depends on the order of the drives as detected by BIOS or UEFI.

I'm not sure it can be changed in the OS but if it can it's probably a very bad idea.

---

### Post by vanadium on 2019-12-27
You do not have a good reason to do this.

---

### Post by crip720 on 2019-12-27
sda/sdb are just names that ubuntu/linux gives to drives when booting up.   Usually sda is the first drive that ubuntu sees when booting up.  Once so often you might notice that drive sda is now sdb.  I think you can change the 'label' names of the the drives in disks, but want someone else to confirm this.  This would only mean that drive sda would be named sdb instead of something else.

---

### Post by oldfred on 2019-12-27
Probably best not to change, but systems now should use UUID, but there may be a few places that device like /dev/sda1 are used.

You can change the SATA ports order. System has to be fully powered down to prevent damage.

Generally sda will be the first drive the system sees, so if one drive is faster it may be sda.
But otherwise drives are in SATA port order, or SATA0 is sda, SATA1 is sdb. Or if not first ports whichever is lowest port is first.
I do have flash drives as sdf become sda when system reboots which changes everything.

---

### Post by rbmorse on 2019-12-27
Like others have mentioned I'm not sure it's a good idea to change, but you can try just swapping the motherboard ports where the data cables connect.  

On my ASUS motherboard the ports are initialized in order so the drive connected to port SATA0 is SDA, the drive connected to port SATA1 is SDB and the drive connected to port SATA4 is SDC.  

Your motherboard manual should tell you how the ports are enumerated, or the port designations may be silkscreened onto the motherboard itself.

---

### Post by TheFu on 2019-12-28
UPDATED  - The Cog pointed out below that */dev/disks* is wrong.  It is **/dev/disk/** as the correct directory.  Thanks for checking.  I've updated this post to correct that hoping to limit confusion. There can already be lots of confusion.

Under the /dev/disk/by-* area are most of the different ways you can access the different storage devices.
```
ls -F  /dev/disk/by-* 
by-id/  by-label/  by-partuuid/  by-path/  by-uuid/

```
Inside each you can see the symbolic links to the different whole disk and partition device names discovered during boot.  Any of those names/labels/tags/UUIDs can be used rather than /dev/sda1.

For example, on one of my systems, 
```
pci-0000:01:00.1-ata-1-part1 -> ../../sda1
```
So, using /dev/disk/by-path/pci-0000:01:00.1-ata-1-part1 is the same as /dev/sda1.  For this specific boot, those two are interchangeable.  The "by-path" will NOT change between boots, unless you physically move a card or cable.

UUID is used commonly in the /etc/fstab, but *LABEL=xyz1234-whatever* works in the /etc/fstab too, assuming you've labelled each partition.

However, if you use ZFS or LVM, these links and names don't work.  You'll need to use the methods used by those specific tools.  LVM uses the Device-Mapper, DM, so all LVs will be in /dev/mapper/  I use LVM, so some examples:
```
$ ls -F1 /dev/mapper/
control
hadar--vg-root@
vg--hadar-lv--backups@
hadar--vg-libvirt--lv@
hadar--vg-swap_1@
hadar--vg-lv--blog44--1604@
hadar--vg-lv--lubuntu11--1604@
hadar--vg-lv--spam3@
hadar--vg-lv--srv--1910@
hadar--vg-lv--vpn09--1604@
hadar--vg-lv--xen41--1604@
hadar--vg-lv--zcs45--1604@
hadar--vg-test--1804@

```
That is on a VM host system where each VM gets an LV block device for virtual storage. Really only the LVs for root, backups, libvirt and swap are used by the host machine and are mounted.  The others are NOT mounted by the host machine, only inside the VM where they are assigned. An example *fstab* mount line is:
```
/dev/mapper/vg--hadar-lv--backups      /Backups     ext4     nofail,noatime,errors=remount-ro 0 1
```
 If you don't use LVM or virtual machines, it is safe to ignore this section.

I wouldn't even try to change the device names. Just don't use them.  There are lots of other options.

---

### Post by The Cog on 2019-12-28
It's /dev/disk not /dev/disks. I just looked because I'm learning too. This gives an interesting output:
```
ls -ld $(find /dev/disk)
```

It might be possible to fix device names with udev persistent naming, but I haven't delved in there. It's too complicated for me, and might not be relevant in more recent distros anyway. But it may be somewhere to start if you really, *really* want to fix the names. You wouldn't be able to change it with a live CD "try Ubuntu" because it's all down to device discovery as the OS boots.

---

