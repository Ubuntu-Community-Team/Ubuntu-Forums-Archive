---
title: "Netboot / PXE Boot Ubuntu anywhere"
date: 2019-02-19
forum: General Help
---

### Post by jam1987 on 2019-02-19
Hello all, 

I've been racking my brain trying to figure this out but no go if any one can help that would be amazing!

I have a FOG server running here for imaging PC's but I would also like to be able to boot Ubuntu across the network on any of these machines for off network management e.g. Virus scan etc.

It acts as a glorified TFTP server with a menu I created using the following boot parameters:

```
[INDENT=2]set path /fog/iso
set nfs_path /var/www/html/fog/iso/ubuntu
kernel http://${fog-ip}${path}/casper/vmlinuz
initrd http://${fog-ip}${path}/casper/initrd.lz || read void
imgargs vmlinuz root=/ boot=casper netboot=nfs nfsroot=${fog-ip}:${nfs_path},vers=4,tcp ip=dhcp splash quiet nfsrootdebug
boot

[/INDENT]

``````
[INDENT=2]set path /fog/iso/15.04_64
set nfs_path /var/www/fog/ISO/15.04_64
kernel http://${fog-ip}${path}/casper/vmlinuz.efi || read void
initrd http://${fog-ip}${path}/casper/initrd.lz || read void
imgargs vmlinuz.efi root=/dev/nfs boot=casper netboot=nfs nfsroot=${fog-ip}:${nfs_path} ip=dhcp splash quiet – || read void
boot || read void
goto start
[/INDENT]

```
Which were followed from here:

[https://wiki.fogproject.org/wiki/index.php/Include_any_ISO_in_the_FOG_Bootmenu#Hirens_15.04](https://wiki.fogproject.org/wiki/index.php/Include_any_ISO_in_the_FOG_Bootmenu#Hirens_15.04)

Using Ubuntu 18 / Ubuntu 15 and they always get to the same spot.

"Kernel Panic - not syncing VFS: Unable to mount root fs on unknown block (0,255)"

No matter what I try as root it never passes this spot.

Etc/exports are like this:

```
[INDENT=2]/var/www/html/fog/iso/ubuntu * (ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)
/var/www/html/fog/iso/15.04_64 * (ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)
[/INDENT]

```
Every boot OK's the vmlinuz and initrd files, it scans the PC fine and then fails at the root error listed above.

Am I missing something stupid or do I need to use an older version of Ubuntu?

Thanks.

---

### Post by jam1987 on 2019-02-20
I've managed to get Ubuntu booting across the network but as an installer only.

Not the live CD portion.

I changed the http:// to tftp:// and moved the vmlinuz and initrd files to the tftp folder.

I also moved the extracted Ubuntu 18 iso to /images/os/ubuntu and now it gets to the install portion on any PC but not the live CD.

My FOG menu item is now:

```

kernel tftp://${fog-ip}/ubuntu/vmlinuz
initrd tftp://${fog-ip}/ubuntu/initrd.gz
imgargs vmlinuz initrd=ubuntu/casper/initrd.lz root=/dev/nfs boot=casper netboot=nfs nfsroot=${fog-ip}:/images/os/ubuntu splash ip=dhcp rw
boot

```

Almost there!

If anyone has any input about what I'm missing or doing wrong to boot the Live CD / Try Ubuntu without installing that would be great!

---

