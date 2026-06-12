---
title: "Dual Boot Question"
date: 2007-09-13
forum: General Help
---

### Post by bswalsh on 2007-09-13
Hi. I'm a new Ubuntu user and so far I love it. I do however need some Windows programs to do my job. WINE won't do what I need because I need native Windows drivers to run my wireless card (ipn2220 64 bit) to it's fullest. For example, NDISWrapper won't support monitor mode. So I think I need to dual boot. The problem is, I took weeks getting Ubuntu just where I want it and have NO desire to format and start over with Windows in the first partition. Also, my copy of Windows XP is on a restore CD, not an install CD. Will I be able to dual boot without losing all of my work? Do I have an option to install my Windows rescue CD as a virtual machine in Ubuntu? If I do dual boot can I install Windows into a new partition from a restore CD without losing my current Ubuntu data? Ideally, I want to use VMWare or something similar so I can use native Windows from my Ubuntu desktop. I'd prefer to never actually boot into Windows. I've searched everywhere but can't find a solution to my specific question. Any help any of you could provide would be a life saver. Thanks!

---

### Post by JKyleOKC on 2007-09-13
I'm running Win XP Pro under VMWare on one Xubuntu box, and Win2K similarly on another. Both seem to work okay although they are slightly slower than they would be if running direct on the hardware.

However I installed both systems from install disks, not restore disks. Many restore disks are full disk images that include all the junk that vendors add to Windows itself.

The good news is that when you install any system under VMWare, it cannot damage your real disks. When you install VMWare, you tell it the maximum disk size it will have to work with. If you have plenty of disk space not yet being used, give it enough to accept everything on the restore disk. VMWare then creates its own disk file, which becomes the virtual hard disk for whatever system you install into it. The restore CD may fill that up with unwanted junk but you can delete it once you have your Windows system in place, and then use something like Ghost or Acronis True Image to make your own "install disk" for any future need.

Googling for "VMWare Ubuntu" without the quotes should get you several pages of links to step by step instructions. Some of the best are right here on the Ubuntu forums! You can use Synaptic to install VMWare easily, and it's smooth sailing from there (although you may have a few questions when it comes time to configure your Windows network settings, since VMWare has a number of ways to deal with the real network card)...

Hope this helps!

---

### Post by bswalsh on 2007-09-13
Thanks! Now I have a new problem. I installed the VMWare Player, realized it was the wrong one, uninstalled it, and tried to install VMWare Server. Now it tells me I have to purge the old version, which I thought I'd done. Now I'm stuck.

---

### Post by maybeway36 on 2007-09-13
[http://www.virtualbox.org/]("http://www.virtualbox.org/")
Use this instead. It has its own apt repository, which is nice.

---

