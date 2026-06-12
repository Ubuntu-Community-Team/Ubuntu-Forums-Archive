---
title: "Problems with Xubuntu dual boot and drive not mounting in win7"
date: 2016-10-08
forum: General Help
---

### Post by d4tyx on 2016-10-08
Hi, scrub here. I "hacked" around this problem a while ago but it's really been getting on my nerves. I have Xubuntu and Win7 on a dual boot setup. I had trouble getting my 1TB internal storage drive to auto mount in xubuntu, so I followed a guide and edited fstab (mnt/1tb) :

[IMG]http://i.imgur.com/027ek0W.png[/IMG]

Which now mounts the drive automatically, but has caused the drive to not auto mount in Win7!
It's worth noting that I had to install grub on both drives (SSD and 1TB storage) using a grub recovery usb due to dual boot/EFI issues from a buggy bios (Lenovo Y500 Notebook). When I turn on the notebook I have to mash F12 boot menu and boot off the storage drive, this is the only way to load grub. Booting off the primary SSD makes the machine hang.

So, when I'm in windows the 1TB does not appear in My Computer, only disk management and is unmounted when Windows starts. Every time I want to mount the drive I have to run a bat script 

sel disk 1
sel part 1
assign letter=d
exit

and restart explorer.exe to make the drive appear. Obviously this is getting pretty annoying, especially when steam and utorrent are expecting that drive to be mounted on startup. Another thing that happens is after booting into Xubuntu, it messes up the Windows 7 paging file if you boot into Windows directly after using Xubuntu, and I get "low memory" issues until I restart Windows!

Any ideas on how to fix these issues? Here are screenshots of the drive setup.

[IMG]http://i.imgur.com/uEpyZx1.png[/IMG]



[IMG]http://i.imgur.com/889tlF6.png[/IMG]
[IMG]http://i.imgur.com/LKHTGPw.png[/IMG]

---

### Post by d4tyx on 2016-10-10
bump

---

### Post by Bucky Ball on 2016-10-10
Welcome. Please copy your fstab file directly from the terminal and paste it in a post here then put code tags around it so it can be read more easily. See the green link in the first line of my signature for how to use them. Thanks.

PS: When posting screen shots please use 'Adv Reply' or 'Go Advanced' and use the paperclip icon in the taskbar there rather than inserting them in the body of your posts. Thanks.

---

