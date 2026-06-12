---
title: "Cloning external drive"
date: 2020-02-25
forum: General Help
---

### Post by ubuntini2 on 2020-02-25
I have an external 2TB NTFS formatted drive that needs cloning.
What is the quickest (and reliable) method to accomplish this?

---

### Post by dragonfly41 on 2020-02-25
There are of course software only cloning tools but a few months back I invested in a [dual bay docking station]("https://cpc.farnell.com/startech/sdock2u33v/usb3-0-dual-bay-ssd-hdd-dock-station/dp/CS31428").

There is also this [optional container]("https://cpc.farnell.com/icy-dock/mb882sp-1s-1b/converter-2-5-sata-ssd-3-5-sata/dp/CS29448?st=EZConvert").

And for harvesting older generation IDE drives I use [this]("https://cpc.farnell.com/startech/sat2ideadp/adaptor-sata-to-ide-for-dock/dp/CS21821?ost=startech+SAT2IDEADP&cfm=true&ddkey=https%3ASearch").

This gives me the flexibility to manage drives.

You need to consider costs, however.

---

### Post by HermanAB on 2020-02-25
Basically, all you need to do is plug both drives in and copy the one to the other with any of several low level file copy commands.  This works because a block device is a 'file' too.

Run dmesg to see what is the usual situation with no extra drives plugged in:
$ su -
password
# dmesg

Then:
Plug the first drive in and run dmesg again to see the name of the device, eg /dev/sdb
Plug the second drive in and run dmesg again, to see the name of the second device, eg /dev/sdc

Finally, copy file sdb to sdc, using the concatenate command:
# cat /dev/sdb > /dev/sdc
...long wait...
#

---

### Post by HermanAB on 2020-02-25
After cloning a NTFS disk, you should probably plug it into a Windows machine to do a file system check.  You cannot do that with NTFS on Linux or Mac.

---

### Post by Skaperen on 2020-02-25
a low-level copy does not make the copied filesystem(s) any more or less consistent than the original, if the copy ran to completion with no errors and the target device is at least as large as the source.  and did i mention that you must be reading and writing the correct devices?

---

### Post by TheFu on 2020-02-25
The target has to be 2TB or larger.  Be careful, since different vendors will make their drive sizes slightly different.
I would use ddrescue and the full HDD device to clone each byte from A --> B.  This gets the partition table, partitions, any encryption container, any volume management (ZFS, LVM), any file systems AND any files on the entire storage device.  It is dumb and will copy every byte, used or not.  That's fine for a HDD that is mostly full.

```
sudo ddrescue /dev/sdX  /dev/sdY   /tmp/log
```
* sdX is the source.
* sdY is the target.
if those are reversed accidentally, all the data you want to clone **will be** gone, wiped.

OTOH, if the HDD is mostly empty, then I'd run **zerofree** on all file systems, then use **fsarchiver** to clone the storage.  Because much of the source disk will have been zero'd out, the compression should be amazing, and faster ... ooops.  zerofree doesn't work on NTFS - sorry.

Why not just use Windows to clone it?

---

