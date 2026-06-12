---
title: "Can't resize windows partition with gparted"
date: 2014-02-15
forum: General Help
---

### Post by jrmchess on 2014-02-15
I have installed ubuntu on my windows xp machine. There is some free space in the windows drive, around 8 gb which I  want to allocate to ubuntu as it is running out of space. So I created a bootable ubuntu usb drive and booted from it. I then ran gparted and tried to resize my windows drive but it gave me an error. It didn't say what the error was but only that an error has occurred. So how do I fix this issue? Thanks

---

### Post by dragonfly41 on 2014-02-15
Here is a bootable windows partition manager.

[http://www.partition-tool.com/resource/manage-partition/usb-partition-manager.htm](http://www.partition-tool.com/resource/manage-partition/usb-partition-manager.htm)

Or staying with GParted ...

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by Mark Phelps on 2014-02-15
If you allocate ALL the free space in your Windows partition, it will most likely CRASH when you go to reboot it.  Windows needs some free space for allocating log files and buffers.

---

### Post by Impavidus on 2014-02-15
Unless this is an ancient 40GB drive, moving 8GB from one partition to another is not going to make a long term difference. Changing the partitions on a drive to use the last few percent of it gives a lot of trouble for very little benefit, as you will still be almost out of space.

---

