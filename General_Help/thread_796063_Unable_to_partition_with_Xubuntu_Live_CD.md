---
title: "Unable to partition with Xubuntu Live CD"
date: 2008-05-16
forum: General Help
---

### Post by SFinn on 2008-05-16
I'm trying to repartition my hard drive. I want to take space from my Ubuntu partition and use it for a new Xubuntu partition. However, whenever I try to alter the Ubuntu partition - using the Xubuntu Live CD - it tells me the drive is still mounted. This happens even after I use GParted to unmount the device.

Anyone got any advice?

---

### Post by bigtony on 2008-05-16
This is a fairly common problem. The xubuntu livecd does mount the ubuntu partition.  Without getting why or how, I'll just tell you you will save yourself a lot of trouble by putting your xubuntu livecd down and burn yourself a copy of  the GParted live CD.  It will work much better for what you are wanting to do, and will let you mess with all the partitions without the errors you may get by trying to force the ubuntu livecd to do this task.

Before you do that though, I just want to make you aware that it's much easier to just install the xfce desktop environment next to your gnome desktop on ubuntu.  Then when you log in, you can pick which desktop environment you want- all in one partition with the same files.  Using the same logic, you can add KDE too. You can install and remove the desktop environments just like any other package. Since they'll install on the same kernel, you will have much less to install and configure.

To sum it up, I would recommend just installing xfce but if you have a reason to have seperate partitions, definately use a gparted livecd in place of the xubuntu livecd you're currently using.

---

### Post by housam on 2008-05-16
+ 1 for the Gparted live CD.

---

### Post by SFinn on 2008-05-16
Actually, the GParted Live CD was my first choice, but I haven't been able to get it to work. I went through about 10mins of questions to establish monitor capabilities and keyboard layout (Standard US all the way), and ended up at one point with various letters bringing up numbers instead, the number keys bringing up symbols, and backspace producing '0.' Hence why I tried using the Xubuntu Live CD instead...

As for just installing the xfce environment, I asked a question in the topic [here]("http://ubuntuforums.org/showthread.php?p=4970452") where I was told Xubuntu would take up less system resources than the Xubuntu-desktop installation. Since my computer is quite low-powered, I figured that it would be better for me to install Xubuntu as a whole new OS. Would you agree?

---

