---
title: "Open a physical partition with qemu"
date: 2007-01-09
forum: General Help
---

### Post by SiCk949 on 2007-01-09
Hello!
First of all, sorry for my english, I'm from spain!.

Well I read some about qemu and now I wanna ask you something: its possible to "open" or "execute" a physical partition with qemu? I think that the answer is yes because I saw it on this wikipedia's article screen: [http://en.wikipedia.org/wiki/KQEMU](http://en.wikipedia.org/wiki/KQEMU) ([http://upload.wikimedia.org/wikipedia/en/3/36/QEMU_Screenshot.png](http://upload.wikimedia.org/wikipedia/en/3/36/QEMU_Screenshot.png))
This is just I wanna do on my Ubuntu 6.10!

Well I need to use some programs of my windows (fireworks, a mysql admin tool, etc) and ofc for test and learn how to run qemu. I searh over google and I only found artciles for load .isos with qemu, I have my window partition installed and perfectly executable.

I have a part. for Ubuntu and another one for Windows (and the swap) so I wanna run the windows partition when I'm on my Ubuntu!.

Another question: Is this a good solution for games with ubuntu installed? a clean well configured xp partition for a few programs / games and you only load it from qemu?

I wish anybody could help me (and many users that have this clue!)
Thanks in advance!!!!

---

### Post by SiCk949 on 2007-01-11
anyone? :(
thanks!

---

### Post by rianquinn on 2007-01-13
I had a hard time understanding your problem, but here the answer I think your looking for. 

You simply can NOT use Qemu to run another partition. You need to run an Image. Or better put you cannot Dual boot, and run Windows in Linux, unless you have a partition with Windows on it, and you have a separate Image with Windows on it. They will be different though, and you will lose more Disk Space.  

Once you load Windows onto a Qemu Image, using a samba File System, or FTP to the host is the best way to share files.

Hope this helps

---

### Post by cookfromfrozen on 2007-01-13
I don't know about QEMU, but you can boot and install to physical partitions in a virtual machine with VMware.

---

