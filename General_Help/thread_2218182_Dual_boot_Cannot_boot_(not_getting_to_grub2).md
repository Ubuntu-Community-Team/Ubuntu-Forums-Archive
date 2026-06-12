---
title: "Dual boot: Cannot boot (not getting to grub2)"
date: 2014-04-19
forum: General Help
---

### Post by nexusvergil on 2014-04-19
Hi all,

I am not able to get to grub to select my OS.  Initially i was getting the grub error "not found", I ran boot-repair and now the laptop just freezes on the HP screen that let's me hit ESC and go to bios, boot from usb, etc.  Here is the boot repair info: paste.Ubuntu.com/7287566.  Thanks for any help!

---

### Post by oldfred on 2014-04-21
Clicky link
[http://paste.ubuntu.com/7287566/](http://paste.ubuntu.com/7287566/)

That link only shows a Windows install. 
You do show space in the extended partition before sda5.
Did you do a Windows recovery or something in Windows that rewrote partition table.
Windows is known to 'forget' to include Linux partitions in an extended partition when it rewrites the partition table.

If so you may be able to recover it with testdisk.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

