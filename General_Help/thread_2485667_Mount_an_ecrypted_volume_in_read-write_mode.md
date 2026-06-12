---
title: "Mount an ecrypted volume in read-write mode"
date: 2023-04-05
forum: General Help
---

### Post by lads on 2023-04-05
I have an external volume encrypted with ext4. I would like to mount it from the command line, but it results in a read-only mount. I am using **usidksctl** for the purpose:

```
$ udisksctl unlock -b /dev/sdd1
Passphrase:
Unlocked /dev/sdd1 as /dev/dm-1.

$ ls -la /dev/mapper
total 0
drwxr-xr-x  2 root root     100 apr  2 12:58 .
drwxr-xr-x 20 root root    4860 apr  2 12:58 ..
crw-------  1 root root 10, 236 mrt 28 19:27 control
lrwxrwxrwx  1 root root       7 apr  2 12:58 luks-1841d2d1-4ce7-46e4-805e-0be262199e7d -> ../dm-1
lrwxrwxrwx  1 root root       7 apr  2 12:53 NOAB -> ../dm-0

$ udisksctl mount -b /dev/mapper/luks-1841d2d1-4ce7-46e4-805e-0be262199e7d
Mounted /dev/dm-1 at /media/user/NOAB

$ cd /media/user/NOAB

$ touch test.txt
touch: cannot touch 'test.txt': Read-only file system
```

Going through the udisksctl manual I understand it takes the same arguments as good old mount. So I gave it a try:

```
$ udisksctl unmount -b /dev/mapper/luks-1841d2d1-4ce7-46e4-805e-0be262199e7d
Unmounted /dev/dm-1.

$ udisksctl mount -o umask=0 -b /dev/mapper/luks-1841d2d1-4ce7-46e4-805e-0be262199e7d
Error mounting /dev/dm-1: GDBus.Error:org.freedesktop.UDisks2.Error.OptionNotPermitted: Mount option `umask=0' is not allowed
```

Is there some other way of passing the **umask** argument to udisksctl? Or any other method to mount the volume in read and write mode?

Thank you.

---

### Post by TheFu on 2023-04-05
You can use **cryptsetup** to open the LUKS container, then mount the file system inside with standard mounts.
When done, do the reverse - **umount** the storage and close the LUKS container using **cryptsetup**.

The manpages are good. For cryptsetup:

```
BASIC COMMANDS
       The following are valid actions for all supported device types.

       **open** <device> <name> --type <device_type>

              Opens (creates a mapping with) <name> backed by device <device>.

              Device type can be plain, luks (default), loopaes or tcrypt.

              For backward compatibility there are open command aliases:

              create (argument-order <name> <device>): open --type plain
              plainOpen: open --type plain
              luksOpen: open --type luks
              loopaesOpen: open --type loopaes
              tcryptOpen: open --type tcrypt

              <options> are type specific and are described below for individual  device
              types.  For  create,  the  order  of  the  <name>  and <device> options is
              inverted for historical  reasons,  all  other  aliases  use  the  standard
              <device> <name> order.

       **close** <name>

              Removes the existing mapping <name> and wipes the key from kernel memory.

              For backward compatibility there are close command aliases: remove, plain&#8208;
              Close, luksClose, loopaesClose, tcryptClose (all behaves exactly the same,
              device type is determined automatically from active device).

              <options> can be [--deferred]
```
Lots more information exists in that manpage.

With an encrypted Ubuntu installation, sda3 is the normal partition that gets take over by the LUKS container. Inside the LUKS container everything is added to an LVM PV, which maps to a VG, and 2 LVs, root, and swap, are typically created.  What this means is that after the LUKS container is open, a **vgchange -ay** command is required for the mapper and LVM to "see" the LVM objects, so they can be accessed by the mount.

Anyway, a little script will make this easy.  I know that the Mate file manager, Caja, supports double-clicking on LUKS objects, will prompt for the unlock passphrase, then automatically activate any LVM objects, which can then be clicked to be mounted.  I don't know if other file managers do this or not. I was actually surprised when caja did it.

LUKS container names must be unique on the system. The same applies for LVM VG names. If there is a conflict, the 2nd VG will not be available, so none of the LVs it holds will be available either.

---

### Post by lads on 2023-04-06
Hi TheFu, thank you for the reply. Below is the log of a new attempt using **cryptsetup**, the result is essentially the same. Could there be something missing?

```
$ sudo cryptsetup open /dev/sdb1 NOABdev
Enter passphrase for /dev/sdb1:
$ sudo vgchange -a y
$ udisksctl mount -b /dev/mapper/NOABdev
Mounted /dev/dm-1 at /media/user/NOAB
$ cd /media/user/NOAB
$ touch test.txt
touch: cannot touch 'test.txt': Read-only file system
```

---

### Post by TheFu on 2023-04-06
Before the mount, run **fsck** on the device holding the file system.  That is probably /dev/mapper/NOABdev, but I don't have enough information to be certain.

After the mount, run
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

It is best to check after each step that it was accomplished correctly when troubleshooting.  For example, I see nothing that says LVM is being used, so the **vgchange** command might not be doing anything.  Cannot tell from the information posted.

---

### Post by MAFoElffen on 2023-04-06
A different perspective. I know that sometimes, while focusing on helping someone, you can get focused on something, and it is easy to overlook things while considering so many things. I know TheFu knows this. I have seen him point this same thing out to others many times. I am just another set of eyes, that has his back (as he has mine).

Something I notice here is that you are mounting to the /media folder. That folder is owned by root. You do not have permissions to write to it unless you either mount it using additional options to mount it as yourself, and set the permissions at the time of the mount... or after the mount is done, then change the permissions and/or ownership of the mount to yourself...

Not trying to hijack the thread, and I know TheFu comes up with some amazing mount options, and is very good at explaining this to User's... So now, taking a step back again to let him explain that.

---

### Post by TheFu on 2023-04-06
I've never used udisksctl ... and avoid using tools other than mount and autofs to manage storage mounts.  Whenever I've tried anything else, it was disappointing.

---

### Post by lads on 2023-04-10
A new attempt, now with the output from **lsblk**.

```
$ udisksctl unlock -b /dev/sdd1
Passphrase:
Unlocked /dev/sdd1 as /dev/dm-2.

$ ls -la /dev/mapper
total 0
drwxr-xr-x  2 root root     120 apr 10 13:09 .
drwxr-xr-x 20 root root    4840 apr 10 13:09 ..
crw-------  1 root root 10, 236 mrt 28 19:27 control
lrwxrwxrwx  1 root root       7 apr 10 13:09 luks-1841d2d1-4ce7-46e4-805e-0be262199e7d -> ../dm-2
lrwxrwxrwx  1 root root       7 apr  2 12:53 NOAB -> ../dm-0
lrwxrwxrwx  1 root root       7 apr 10 13:04 NOAB2 -> ../dm-1

$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                                            SIZE TYPE  FSTYPE      MOUNTPOINT
sdd                                           465,8G disk
&#9492;&#9472;sdd1                                        465,8G part  crypto_LUKS
  &#9492;&#9472;luks-1841d2d1-4ce7-46e4-805e-0be262199e7d 465,7G crypt ext4

$ udisksctl mount -b /dev/mapper/luks-1841d2d1-4ce7-46e4-805e-0be262199e7d
Mounted /dev/dm-2 at /media/user/NOAB

$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                                            SIZE TYPE  FSTYPE      MOUNTPOINT
sdd                                           465,8G disk
&#9492;&#9472;sdd1                                        465,8G part  crypto_LUKS
  &#9492;&#9472;luks-1841d2d1-4ce7-46e4-805e-0be262199e7d 465,7G crypt ext4        /media/user/NOAB

$ touch /media/user/NOAB/test.txt
touch: cannot touch '/media/user/NOAB/test.txt': Read-only file system
```

---

### Post by TheFu on 2023-04-10
Try doing it without using udisksctl

---

### Post by lads on 2023-04-11
In the end it was about simplifying, as TheFu suggested, solution is in the log below. Before that, just to answer MAFoElffen, by default volumes mounted to */media/user* are accessible to users. Mount options control permissions.

The basic solution, combining **cryptsetup** and **mount**:

```

$ sudo cryptsetup open /dev/sdd1 NOABdev
Enter passphrase for /dev/sdd1:

$ mkdir -p ~/mount/test

$ sudo mount /dev/mapper/NOABdev ~/mount/test

$ touch ~/mount/test/test.txt

```

Now mounting to */media/user* with root:

```

$ sudo umount ~/mount/test

$ sudo mkdir /media/user/NOAB

$ sudo mount /dev/mapper/NOABdev2 /media/user/NOAB

$ touch /media/user/NOAB/test2.txt

```

Thank you all for replies.

---

