---
title: "Mount point info show a &quot;1&quot; added end of the UUID partition id under DISKS app?"
date: 2023-07-18
forum: General Help
---

### Post by ozark_hillbilly on 2023-07-18
Hello,

Why does DISKS app show a "1" added to the end of the mount point UUID descriptor?

Screenshot provided...

thanks....


edit -

Now I am really confused. After running Backups app and it completed successfully with no errors I have no files in the destination directory  (0 items). ????
If I go to Backups and under Restore look at the destination folder it shows all the duplicity backup files under the UUID without the extra "1" at the end.
The folder listed under the UUID with the extra "1" at the end is blank. 
Why is this set up like this?
Using the FILES app the destination directory is empty. ???

see additional screenshots.....

---

### Post by deadflowr on 2023-07-18
It's adding an extra number because the mountpoint name already exists as a directory in /media.

Look at ```
ls /media/ed
```
to see what directories exist.

---

### Post by ozark_hillbilly on 2023-07-18
I just added additional info to my original post as Backups app has put the backed up data in the UUID without an etra "1" and under FILES app that folder is empty. I am confused unfortunately.

---

### Post by ozark_hillbilly on 2023-07-18
Here is ls ls /media/Ed output:


screenshot attached....

Is it ok to just delete the extra directory with the additional "1" at the end of the UUID without creating any heartaches for the system?

---

### Post by deadflowr on 2023-07-19
It's easier to read when you copy and paste it in to a new post.
> Is it ok to just delete the extra directory with the additional "1" at the end of the UUID without creating any heartaches for the system?
I'd say it is okay to delete only after you have made quadruple sure that nothing is mounted there with any important files.

---

### Post by ozark_hillbilly on 2023-07-19
thank you...

---

### Post by ozark_hillbilly on 2023-07-19
thank you for the explanation....

---

### Post by MAFoElffen on 2023-07-19
> **deadflowr said:**
> It's easier to read when you copy and paste it in to a new post.
[COLOR=#ff0000]I'd say it is okay to delete only after you have made quadruple sure that nothing is mounted there with any important files.[/COLOR]
He actually meant: "NO". Do not delete it.

You know that something "can be" mounted multitple places into your filesystem at once right? Only one source can be mounted to one directory mountpoint tag at a time, 

This has come up in multiple threads lately, so I think an explanation is in order. Mounting does have some restrictions, and caveats:
The mount point must be a directory. If it is not an empty directory, files in that directory are not accessible while the file system is mounted. So you can make a mount over a non-empty directory, but that will mask what is there already. This problem has occurred many time here, usually when someone is trying to create a new mounted Home folder. This also affects users who are creating BTRFS subvolumes, ZFS datasets, and mounting them back into their filesystems... Be aware of the mountpoint and what is there (before and after).

Only one file system can be mounted at a directory (mount point) at any one time. (See above)

Systems participating in shared file system capability "can" mount file systems that will be shared in read/write mode. But the initial mount, unless otherwise specified, is usually owned by root, with root permissions. You need to give read/write permissions to be able write to it, by other than root. (unless that has already been given previously)

The source can be mounted into the filesystem to multiple mountpoints at the same time... If it has different mount names (not the same name).

So look at this example from my server:
```

mafoelffen@Mikes-B460M:~$ findmnt | grep -v -e 'nsfs\|squashfs\|tmpfs\|fuse\|snap\|sys\|run\|proc\|devpts\|mqueue\|hugetlbfs'
TARGET                                            SOURCE                                           FSTYPE          OPTIONS
/                                                 rpool/ROOT/ubuntu_2cwpns                         zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/root                                           rpool/USERDATA/root_gtg9x1                       zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/home/mafoelffen                                rpool/USERDATA/mafoelffen_gtg9x1                 zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/usr/local                                      rpool/ROOT/ubuntu_2cwpns/usr/local               zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/srv                                            rpool/ROOT/ubuntu_2cwpns/srv                     zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/var/lib                                        rpool/ROOT/ubuntu_2cwpns/var/lib                 zfs             rw,relatime,xattr,posixacl
&#9474; &#9500;&#9472;/var/lib/NetworkManager                       rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager  zfs             rw,relatime,xattr,posixacl
&#9474; &#9500;&#9472;/var/lib/apt                                  rpool/ROOT/ubuntu_2cwpns/var/lib/apt             zfs             rw,relatime,xattr,posixacl
&#9474; &#9500;&#9472;/var/lib/dpkg                                 rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg            zfs             rw,relatime,xattr,posixacl
&#9474; &#9492;&#9472;/var/lib/AccountsService                      rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/var/log                                        rpool/ROOT/ubuntu_2cwpns/var/log                 zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/var/games                                      rpool/ROOT/ubuntu_2cwpns/var/games               zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/var/mail                                       rpool/ROOT/ubuntu_2cwpns/var/mail                zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/var/spool                                      rpool/ROOT/ubuntu_2cwpns/var/spool               zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/var/www                                        rpool/ROOT/ubuntu_2cwpns/var/www                 zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/boot                                           bpool/BOOT/ubuntu_2cwpns                         zfs             rw,nodev,relatime,xattr,posixacl
&#9474; &#9500;&#9472;/boot/efi                                     /dev/nvme4n1p1                                   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
&#9474; &#9492;&#9472;/boot/grub                                    /dev/nvme4n1p1[/grub]                            vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
&#9500;&#9472;/KVM_Pool                                       kpool/KVM/ubuntu_2cwpns                          zfs             rw,relatime,xattr,posixacl
&#9500;&#9472;/data                                           datapool/DATA/ubuntu_2cwpns                      zfs             rw,relatime,xattr,posixacl
&#9474; &#9500;&#9472;/data/KVM-VM                                  datapool/DATA/ubuntu_2cwpns/KVM-VM               zfs             rw,relatime,xattr,posixacl
&#9474; &#9492;&#9472;/data/ISO                                     datapool/DATA/ubuntu_2cwpns/ISO                  zfs             rw,relatime,xattr,posixacl

```
You see where my EFI partition is mounted to both /boot/efi and /boot/grub, right?

So if yours is mounted in two places, yes... If you delete something there in either of the mountpoints, then it does affect the original source. So please heed his warning to check what you are deleting, before you do that.

---

