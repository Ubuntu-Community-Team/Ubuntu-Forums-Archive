---
title: "having problem resizing ext4 partition"
date: 2017-03-18
forum: General Help
---

### Post by alexkoganov on 2017-03-18
hi guys
i am using Gparted on live ubuntu and i cand allocate more space to ext4 partition even if i have a lot of unallocated space.

i attached a prt sc of it

tnx a lot

---

### Post by howefield on 2017-03-18
You would need to move sda3 to the left so the unallocated space was adjacent to one you want to resize, in this case sda4.

---

### Post by alexkoganov on 2017-03-19
so after i moved sda3 to the left and resized the ext4 partition my ubuntu is dead :).
after i restarted my laptop and tried to run ubuntu there's a lot of errors occurred (see the link i provided) : [https://app.box.com/s/0aqfw644iu2ohnsyy4oh8js0wlviy7bi](https://app.box.com/s/0aqfw644iu2ohnsyy4oh8js0wlviy7bi).
now that i thinking about it there was some warning when i resized the ext4 partition that warned me that afetr the resizing my os maybe whould no load.
why is that and what wrong?

tnx a lot

---

### Post by deadflowr on 2017-03-19
Boot the live session again and post another screenshot from gparted.
As well, follow these to run boot-info and post the pastebin link it provides.
Boot Repair[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Boot Info [https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

for now, just run the boot-info option.

---

### Post by alexkoganov on 2017-03-19
hi
see screenshots

tnx

and see also the message from boot repair tool

tnx


[http://paste2.org/YMB0g7hg]("http://paste2.org/YMB0g7hg")

---

### Post by deadflowr on 2017-03-19
Seems it's a corruption when you moved things around.
perhaps run a filesystem check.
more on that here:
[https://help.ubuntu.com/community/FilesystemTroubleshooting]("https://help.ubuntu.com/community/FilesystemTroubleshooting")

---

### Post by alexkoganov on 2017-03-20
i gave up and reinstall ubuntu but now i cant see the option to launch  win 10 in grub menu.
used this guide :
[http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot](http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot)

also see the screen shot from gparted..
the both ntfs partition are exist.

tnx a lot

---

