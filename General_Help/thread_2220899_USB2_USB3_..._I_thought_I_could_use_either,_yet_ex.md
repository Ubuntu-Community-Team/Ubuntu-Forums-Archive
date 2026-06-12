---
title: "USB2 USB3 ... I thought I could use either, yet external HD only connect to USB2"
date: 2014-04-29
forum: General Help
---

### Post by xigen on 2014-04-29
I built a new system w/ USB2 and USB3 connections.  

When I plug my BlacX (external HD) into a USB2 slot ... it works.  When I use a USB3 slot the system (ubuntu 13.10) does not 'see' the drive. 

Thoughts?

Also, I am considering getting a cable (eSATA-->USB3); however, if USB3 is an issue with the drive then I wonder if the use of eSATA makes any sense.

Thoughts?

Here is the output of $mount.
I have two external drives plugged in; one with a single HD, and one with the capacity for two HD.
```

meow@meow:~/Downloads/Bitwi$ mount
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=meow)
/dev/sdb1 on /media/meow/littlemeow type ext4 (rw,nosuid,nodev,uhelper=udisks2)
gvfsd-fuse on /home/meow/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
/dev/sdc1 on /media/meow/BigMeow type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

---

### Post by sudodus on 2014-04-30
I have good experience of eSATA. But connect it to one of your SATA ports via a simple 'PCI bracket cable', for example this one

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812226003](http://www.newegg.com/Product/Product.aspx?Item=N82E16812226003)

without involving USB (if possible).

---

### Post by HermanAB on 2014-04-30
To get some clues:

Unplug the disk
$ dmesg

Plug the disk into the USB3 port
$ dmesg

You can also try:
$ lsusb

Google what you see or ask again here and hope someone knows something.

---

### Post by xigen on 2014-04-30
```
$ dmesg (unplugged)
```
then 
```
$ dmesg (plugged into usb3)
$ Lsusb

[    1.473381] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473382] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473383] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473385] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473386] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473387] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473388] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473390] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473391] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473392] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473393] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473395] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473396] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473397] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473398] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473400] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473401] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473402] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473403] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473405] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473406] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473407] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473409] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473410] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473411] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473412] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473414] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473415] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473416] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473417] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473419] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473420] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473421] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473422] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473424] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473425] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473426] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473427] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473429] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473430] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473431] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473432] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473434] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473435] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473436] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473437] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473439] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473440] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473441] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473442] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473444] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473445] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473446] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473447] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473449] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473450] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473451] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473453] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473454] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473455] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473456] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473458] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473459] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473460] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473461] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473463] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473464] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473465] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473466] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473468] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473469] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473470] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473471] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473473] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473474] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473475] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473476] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473478] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473479] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473480] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473481] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473483] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473484] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473485] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473486] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473488] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473489] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473490] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473492] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473493] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473494] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473495] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473497] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473498] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473499] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473500] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473502] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473503] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473504] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473505] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473507] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473508] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473509] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473510] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473512] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473513] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473514] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473515] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473517] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473518] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473519] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473520] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473522] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473523] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473524] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473525] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473527] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473528] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473529] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473530] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473532] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473533] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473534] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473536] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473537] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473538] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473539] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473541] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473542] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473543] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473544] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473546] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473547] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473548] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473549] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473551] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473552] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473553] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473554] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473556] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473557] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473558] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473559] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473561] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473562] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473563] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473564] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473566] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473567] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473568] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473569] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473571] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473572] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473573] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473574] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473576] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473577] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473578] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473579] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473581] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473582] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473583] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.473585] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0012 address=0x00000000bea106c0 flags=0x0010]
[    1.544404] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.677798] usb 3-1: New USB device found, idVendor=05e3, idProduct=0608
[    1.677801] usb 3-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.677802] usb 3-1: Product: USB2.0 Hub
[    1.678189] hub 3-1:1.0: USB hub found
[    1.678552] hub 3-1:1.0: 4 ports detected
[    1.792178] usb 3-2: new high-speed USB device number 3 using ehci-pci
[    1.925824] usb 3-2: New USB device found, idVendor=152d, idProduct=2336
[    1.925826] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[    1.925828] usb 3-2: Product: JM20336 SATA, USB Combo
[    1.925829] usb 3-2: Manufacturer: JMicron
[    1.925830] usb 3-2: SerialNumber: 6C7698888888
[    1.996254] usb 3-1.2: new low-speed USB device number 4 using ehci-pci
[    2.113024] usb 3-1.2: New USB device found, idVendor=06a3, idProduct=8021
[    2.113026] usb 3-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.113028] usb 3-1.2: Product: Saitek Eclipse II Keyboard
[    2.113029] usb 3-1.2: Manufacturer: Chicony
[    2.147893] tsc: Refined TSC clocksource calibration: 3516.104 MHz
[    2.184203] usb 3-1.3: new full-speed USB device number 5 using ehci-pci
[    2.278994] usb 3-1.3: New USB device found, idVendor=1a7c, idProduct=0191
[    2.278996] usb 3-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.278998] usb 3-1.3: Product: Evoluent VerticalMouse 4
[   18.541616] xhci_hcd 0000:01:00.0: can't setup
[   18.541620] xhci_hcd 0000:01:00.0: USB bus 8 deregistered
[   18.541637] Switched to clocksource tsc
[   18.541689] xhci_hcd 0000:01:00.0: init 0000:01:00.0 fail, -110
[   18.541694] xhci_hcd: probe of 0000:01:00.0 failed with error -110
[   18.541737] i8042: PNP: No PS/2 controller found. Probing ports directly.
[   18.542106] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.542111] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.542229] mousedev: PS/2 mouse device common for all mice
[   18.542329] rtc_cmos 00:05: RTC can wake from S4
[   18.542410] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   18.542429] rtc_cmos 00:05: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[   18.542481] device-mapper: uevent: version 1.0.3
[   18.542526] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[   18.542615] cpuidle: using governor ladder
[   18.542741] cpuidle: using governor menu
[   18.542751] ledtrig-cpu: registered to indicate activity on CPUs
[   18.542819] TCP: cubic registered
[   18.542897] NET: Registered protocol family 10
[   18.543056] NET: Registered protocol family 17
[   18.543066] Key type dns_resolver registered
[   18.543493] PM: Hibernation image not present or could not be loaded.
[   18.543496] Loading module verification certificates
[   18.544236] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 5553b4b7b74ebe0a90f93fbc0d8e2b9c98211b47'
[   18.544244] registered taskstats version 1
[   18.546826] Key type trusted registered
[   18.548912] Key type encrypted registered
[   18.550749] AppArmor: AppArmor sha1 policy hashing enabled
[   18.551037]   Magic number: 10:711:214
[   18.551092] rtc_cmos 00:05: setting system clock to 2014-04-27 05:14:55 UTC (1398575695)
[   18.551205] acpi-cpufreq: overriding BIOS provided _PSD data
[   18.551527] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.551528] EDD information not available.
[   18.552515] Freeing unused kernel memory: 1368K (ffffffff81d10000 - ffffffff81e66000)
[   18.552517] Write protecting the kernel read-only data: 12288k
[   18.555042] Freeing unused kernel memory: 1028K (ffff8800016ff000 - ffff880001800000)
[   18.556882] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[   18.568353] systemd-udevd[149]: starting version 204
[   18.580462] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   18.580475] ahci 0000:00:11.0: version 3.0
[   18.580482] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   18.580812] r8169 0000:02:00.0: irq 73 for MSI/MSI-X
[   18.581040] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c1a000, 74:d4:35:5e:c7:63, XID 0c900800 IRQ 73
[   18.581042] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   18.581414] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[   18.581418] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[   18.582202] scsi0 : ahci
[   18.582341] scsi1 : ahci
[   18.582510] scsi2 : ahci
[   18.582620] scsi3 : ahci
[   18.582704] ata1: SATA max UDMA/133 abar m1024@0xfe307000 port 0xfe307100 irq 19
[   18.582706] ata2: SATA max UDMA/133 abar m1024@0xfe307000 port 0xfe307180 irq 19
[   18.582708] ata3: SATA max UDMA/133 abar m1024@0xfe307000 port 0xfe307200 irq 19
[   18.582710] ata4: SATA max UDMA/133 abar m1024@0xfe307000 port 0xfe307280 irq 19
[   18.585152] scsi4 : pata_atiixp
[   18.585382] scsi5 : pata_atiixp
[   18.585457] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   18.585459] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   18.587944] usb-storage 3-2:1.0: USB Mass Storage device detected
[   18.588283] scsi6 : usb-storage 3-2:1.0
[   18.588355] hidraw: raw HID events driver (C) Jiri Kosina
[   18.588391] usbcore: registered new interface driver usb-storage
[   18.616514] usbcore: registered new interface driver usbhid
[   18.616520] usbhid: USB HID core driver
[   18.618054] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:16.2/usb3/3-1/3-1.2/3-1.2:1.0/input/input2
[   18.618139] hid-generic 0003:06A3:8021.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:16.2-1.2/input0
[   18.624361] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:16.2/usb3/3-1/3-1.2/3-1.2:1.1/input/input3
[   18.624567] hid-generic 0003:06A3:8021.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:16.2-1.2/input1
[   18.624748] input: Evoluent VerticalMouse 4 as /devices/pci0000:00/0000:00:16.2/usb3/3-1/3-1.3/3-1.3:1.0/input/input4
[   18.624855] hid-generic 0003:1A7C:0191.0003: input,hidraw2: USB HID v1.11 Mouse [Evoluent VerticalMouse 4] on usb-0000:00:16.2-1.3/input0
[   18.898671] ata1: SATA link down (SStatus 0 SControl 300)
[   18.902652] ata4: SATA link down (SStatus 0 SControl 300)
[   19.074502] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.074536] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   19.077797] ata3.00: ATAPI: ASUS    DRW-24B1ST   i, 1.00, max UDMA/100
[   19.078642] ata3.00: configured for UDMA/100
[   19.089175] ata2.00: ATA-9: INTEL SSDSC2BW240A4, DC32, max UDMA/133
[   19.089183] ata2.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[   19.115521] ata2.00: configured for UDMA/133
[   19.115864] scsi 1:0:0:0: Direct-Access     ATA      INTEL SSDSC2BW24 DC32 PQ: 0 ANSI: 5
[   19.116042] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   19.116088] sd 1:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[   19.116193] sd 1:0:0:0: [sda] Write Protect is off
[   19.116196] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.116228] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.116860]  sda: sda1 sda2 < sda5 >
[   19.117245] sd 1:0:0:0: [sda] Attached SCSI disk
[   19.121439] scsi 2:0:0:0: CD-ROM            ASUS     DRW-24B1ST   i   1.00 PQ: 0 ANSI: 5
[   19.124349] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.124356] cdrom: Uniform CD-ROM driver Revision: 3.20
[   19.124661] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   19.124736] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   19.166524] bio: create slab <bio-1> at 1
[   19.188662] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[   19.188665] EXT4-fs (dm-0): write access will be enabled during recovery
[   19.360556] EXT4-fs (dm-0): recovery complete
[   19.371262] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   19.551478] Adding 8351740k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:8351740k SSFS
[   19.567090] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.586815] scsi 6:0:0:0: Direct-Access     ST925031 5AS                   PQ: 0 ANSI: 2 CCS
[   19.586982] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   19.587566] sd 6:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[   19.588804] sd 6:0:0:0: [sdb] Write Protect is off
[   19.588807] sd 6:0:0:0: [sdb] Mode Sense: 00 38 00 00
[   19.590057] sd 6:0:0:0: [sdb] Asking for cache data failed
[   19.590118] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   19.593307] sd 6:0:0:0: [sdb] Asking for cache data failed
[   19.593366] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   19.594547]  sdb: sdb1 sdb2 < sdb5 >
[   19.597574] systemd-udevd[363]: starting version 204
[   19.598171] sd 6:0:0:0: [sdb] Asking for cache data failed
[   19.598235] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   19.598295] sd 6:0:0:0: [sdb] Attached SCSI disk
[   19.684452] lp: driver loaded but no devices found
[   19.716093] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   19.716839] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   19.717445] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   19.717498] sp5100_tco: PCI Revision ID: 0x42
[   19.717535] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   19.717547] sp5100_tco: Last reboot was not triggered by watchdog.
[   19.718125] sp5100_tco: initialized (0xffffc90000c3cb00). heartbeat=60 sec (nowayout=0)
[   19.728318] [drm] Initialized drm 1.1.0 20060810
[   19.729918] MCE: In-kernel MCE decoding enabled.
[   19.731855] EDAC MC: Ver: 3.0.0
[   19.733357] AMD64 EDAC driver v3.4.0
[   19.733406] EDAC amd64: DRAM ECC disabled.
[   19.733419] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   19.733419]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   19.733419]  (Note that use of the override may cause unknown side effects.)
[   19.743010] nvidia: module license 'NVIDIA' taints kernel.
[   19.743014] Disabling lock debugging due to kernel taint
[   19.750380] type=1400 audit(1398575696.695:2): apparmor="STATUS" operation="profile_load" parent=428 profile="unconfined" name="/sbin/dhclient" pid=460 comm="apparmor_parser"
[   19.750390] type=1400 audit(1398575696.695:3): apparmor="STATUS" operation="profile_load" parent=428 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   19.750396] type=1400 audit(1398575696.695:4): apparmor="STATUS" operation="profile_load" parent=428 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   19.750886] type=1400 audit(1398575696.695:5): apparmor="STATUS" operation="profile_replace" parent=428 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   19.750894] type=1400 audit(1398575696.695:6): apparmor="STATUS" operation="profile_replace" parent=428 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   19.751142] type=1400 audit(1398575696.695:7): apparmor="STATUS" operation="profile_replace" parent=428 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   19.753057] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   19.755188] microcode: CPU0: patch_level=0x06000822
[   19.759107] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.760752] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:04:00.0 on minor 0
[   19.760761] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.32  Wed Jun 19 15:51:20 PDT 2013
[   19.777820] hda_intel: Disabling MSI
[   19.777832] hda-intel 0000:04:00.1: Handle VGA-switcheroo audio client
[   19.777873] hda-intel 0000:04:00.1: Disabling 64bit DMA
[   19.781377] hda-intel 0000:04:00.1: Enable delay in RIRB handling
[   19.840181] microcode: CPU1: patch_level=0x06000822
[   19.840191] microcode: CPU2: patch_level=0x06000822
[   19.840200] microcode: CPU3: patch_level=0x06000822
[   19.840209] microcode: CPU4: patch_level=0x06000822
[   19.840217] microcode: CPU5: patch_level=0x06000822
[   19.840227] microcode: CPU6: patch_level=0x06000822
[   19.840239] microcode: CPU7: patch_level=0x06000822
[   19.840306] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   19.874555] kvm: Nested Virtualization enabled
[   19.874562] kvm: Nested Paging enabled
[   19.929324] init: failsafe main process (654) killed by TERM signal
[   19.990577] Bluetooth: Core ver 2.16
[   19.990596] NET: Registered protocol family 31
[   19.990598] Bluetooth: HCI device and connection manager initialized
[   19.990606] Bluetooth: HCI socket layer initialized
[   19.990609] Bluetooth: L2CAP socket layer initialized
[   19.990614] Bluetooth: SCO socket layer initialized
[   19.993486] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.993489] Bluetooth: BNEP filters: protocol multicast
[   19.993495] Bluetooth: BNEP socket layer initialized
[   19.995880] Bluetooth: RFCOMM TTY layer initialized
[   19.995892] Bluetooth: RFCOMM socket layer initialized
[   19.995894] Bluetooth: RFCOMM ver 1.11
[   20.024247] type=1400 audit(1398575696.967:8): apparmor="STATUS" operation="profile_load" parent=798 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=805 comm="apparmor_parser"
[   20.024257] type=1400 audit(1398575696.967:9): apparmor="STATUS" operation="profile_load" parent=798 profile="unconfined" name="chromium_browser" pid=805 comm="apparmor_parser"
[   20.024639] type=1400 audit(1398575696.967:10): apparmor="STATUS" operation="profile_replace" parent=798 profile="unconfined" name="chromium_browser" pid=805 comm="apparmor_parser"
[   20.024931] type=1400 audit(1398575696.967:11): apparmor="STATUS" operation="profile_load" parent=798 profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=806 comm="apparmor_parser"
[   20.041949] init: avahi-cups-reload main process (808) terminated with status 1
[   20.042681] ppdev: user-space parallel port driver
[   20.215602] r8169 0000:02:00.0 eth0: link down
[   20.215618] r8169 0000:02:00.0 eth0: link down
[   20.215654] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.215886] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.217636] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:15.0/0000:04:00.1/sound/card0/input5
[   20.217718] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:15.0/0000:04:00.1/sound/card0/input6
[   20.217786] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:15.0/0000:04:00.1/sound/card0/input7
[   20.861676] init: udev-fallback-graphics main process (1242) terminated with status 1
[   20.898395] init: plymouth-splash main process (1260) terminated with status 1
[   22.508836] r8169 0000:02:00.0 eth0: link up
[   22.508845] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.878894] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[  285.346694] audit_printk_skb: 174 callbacks suppressed
[  285.346702] type=1400 audit(1398575959.677:70): apparmor="STATUS" operation="profile_replace" parent=2773 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2777 comm="apparmor_parser"
[  285.346718] type=1400 audit(1398575959.677:71): apparmor="STATUS" operation="profile_replace" parent=2773 profile="unconfined" name="/usr/sbin/cupsd" pid=2777 comm="apparmor_parser"
[  285.347916] type=1400 audit(1398575959.677:72): apparmor="STATUS" operation="profile_replace" parent=2773 profile="unconfined" name="/usr/sbin/cupsd" pid=2777 comm="apparmor_parser"
[  375.095722] r8169 0000:02:00.0 eth0: link down
[  379.450237] r8169 0000:02:00.0 eth0: link up
[ 1737.997689] systemd-hostnamed[3265]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3605.493169] systemd-hostnamed[3616]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 4779.287245] systemd-hostnamed[4303]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[35232.880571] type=1400 audit(1398610934.989:73): apparmor="STATUS" operation="profile_replace" parent=14795 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=14799 comm="apparmor_parser"
[35232.880590] type=1400 audit(1398610934.989:74): apparmor="STATUS" operation="profile_replace" parent=14795 profile="unconfined" name="/usr/sbin/cupsd" pid=14799 comm="apparmor_parser"
[35232.881781] type=1400 audit(1398610934.989:75): apparmor="STATUS" operation="profile_replace" parent=14795 profile="unconfined" name="/usr/sbin/cupsd" pid=14799 comm="apparmor_parser"
[57836.482894] systemd-hostnamed[16057]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[58008.364362] usb 2-1: new high-speed USB device number 2 using ehci-pci
[58008.497234] usb 2-1: New USB device found, idVendor=152d, idProduct=2352
[58008.497241] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[58008.497246] usb 2-1: Product: USB to ATA/ATAPI Bridge
[58008.497250] usb 2-1: Manufacturer: JMicron
[58008.497253] usb 2-1: SerialNumber: 6E0FF3FFFFFF
[58008.498086] usb-storage 2-1:1.0: USB Mass Storage device detected
[58008.498312] scsi7 : usb-storage 2-1:1.0
[58009.496220] scsi 7:0:0:0: Direct-Access     ST310003 33AS                  PQ: 0 ANSI: 2 CCS
[58009.496689] sd 7:0:0:0: Attached scsi generic sg3 type 0
[58009.498088] sd 7:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[58009.499208] sd 7:0:0:0: [sdc] Write Protect is off
[58009.499217] sd 7:0:0:0: [sdc] Mode Sense: 34 00 00 00
[58009.500217] sd 7:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[58009.517140]  sdc: sdc1
[58009.521108] sd 7:0:0:0: [sdc] Attached SCSI disk
[58022.691233] Buffer I/O error on device sdc1, logical block 3
[58022.691248] Buffer I/O error on device sdc1, logical block 3
[58022.691258] Buffer I/O error on device sdc1, logical block 3
[58022.691268] Buffer I/O error on device sdc1, logical block 3
[58022.691280] Buffer I/O error on device sdc1, logical block 7
[58022.691290] Buffer I/O error on device sdc1, logical block 7
[58022.691299] Buffer I/O error on device sdc1, logical block 7
[58022.691308] Buffer I/O error on device sdc1, logical block 7
[58022.691320] Buffer I/O error on device sdc1, logical block 15
[58022.691329] Buffer I/O error on device sdc1, logical block 15
[58022.697329] usb 2-1: USB disconnect, device number 2
[58056.781841] usb 2-1: new high-speed USB device number 3 using ehci-pci
[58056.914648] usb 2-1: New USB device found, idVendor=152d, idProduct=2352
[58056.914656] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[58056.914661] usb 2-1: Product: USB to ATA/ATAPI Bridge
[58056.914665] usb 2-1: Manufacturer: JMicron
[58056.914668] usb 2-1: SerialNumber: 6E0FF3FFFFFF
[58056.915465] usb-storage 2-1:1.0: USB Mass Storage device detected
[58056.915654] scsi8 : usb-storage 2-1:1.0
[58057.913508] scsi 8:0:0:0: Direct-Access     ST310003 33AS                  PQ: 0 ANSI: 2 CCS
[58057.914070] sd 8:0:0:0: Attached scsi generic sg3 type 0
[58057.915430] sd 8:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[58057.916490] sd 8:0:0:0: [sdc] Write Protect is off
[58057.916500] sd 8:0:0:0: [sdc] Mode Sense: 34 00 00 00
[58057.921176] sd 8:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[58057.940622]  sdc: sdc1
[58057.944964] sd 8:0:0:0: [sdc] Attached SCSI disk
[69500.128335] systemd-hostnamed[17977]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[70567.027338] systemd-hostnamed[19639]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[75987.766264] systemd-hostnamed[22315]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[87876.802162] systemd-hostnamed[25706]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[91130.786580] systemd-hostnamed[26064]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[121292.942481] audit_printk_skb: 34 callbacks suppressed
[121292.942485] type=1400 audit(1398697063.495:76): apparmor="STATUS" operation="profile_replace" parent=28174 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=28178 comm="apparmor_parser"
[121292.942493] type=1400 audit(1398697063.495:77): apparmor="STATUS" operation="profile_replace" parent=28174 profile="unconfined" name="/usr/sbin/cupsd" pid=28178 comm="apparmor_parser"
[121292.942979] type=1400 audit(1398697063.495:78): apparmor="STATUS" operation="profile_replace" parent=28174 profile="unconfined" name="/usr/sbin/cupsd" pid=28178 comm="apparmor_parser"
[157765.203244] systemd-hostnamed[2511]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[207434.112990] type=1400 audit(1398783273.181:79): apparmor="STATUS" operation="profile_replace" parent=4714 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=4718 comm="apparmor_parser"
[207434.113009] type=1400 audit(1398783273.181:80): apparmor="STATUS" operation="profile_replace" parent=4714 profile="unconfined" name="/usr/sbin/cupsd" pid=4718 comm="apparmor_parser"
[207434.114202] type=1400 audit(1398783273.181:81): apparmor="STATUS" operation="profile_replace" parent=4714 profile="unconfined" name="/usr/sbin/cupsd" pid=4718 comm="apparmor_parser"
[231884.156926] systemd-hostnamed[5683]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[234924.267057] usb 3-1.3: input irq status -75 received
[247342.315114] systemd-hostnamed[8455]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[250550.992669] systemd-hostnamed[8999]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[293066.856649] type=1400 audit(1398868974.031:82): apparmor="STATUS" operation="profile_replace" parent=10000 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=10004 comm="apparmor_parser"
[293066.856669] type=1400 audit(1398868974.031:83): apparmor="STATUS" operation="profile_replace" parent=10000 profile="unconfined" name="/usr/sbin/cupsd" pid=10004 comm="apparmor_parser"
[293066.857867] type=1400 audit(1398868974.031:84): apparmor="STATUS" operation="profile_replace" parent=10000 profile="unconfined" name="/usr/sbin/cupsd" pid=10004 comm="apparmor_parser"
[294959.375644] systemd-hostnamed[10142]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[294972.770225] usb 2-1: USB disconnect, device number 3
[294972.811964] sd 8:0:0:0: [sdc] Unhandled error code
[294972.811972] sd 8:0:0:0: [sdc]  
[294972.811975] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[294972.811979] sd 8:0:0:0: [sdc] CDB: 
[294972.811982] Read(10): 28 00 74 70 67 80 00 00 08 00
[294972.811997] end_request: I/O error, dev sdc, sector 1953523584
[294972.812003] Buffer I/O error on device sdc1, logical block 244189936
meow@meow:~/Downloads/Bitwi$ lsusb
Bus 003 Device 003: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. Hard Disk Drive
Bus 003 Device 005: ID 1a7c:0191 Evoluent VerticalMouse 4
Bus 003 Device 004: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

