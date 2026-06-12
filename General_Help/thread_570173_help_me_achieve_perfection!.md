---
title: "help me achieve perfection!"
date: 2007-10-07
forum: General Help
---

### Post by manichean on 2007-10-07
I've always been a capable computer user knowing that one day I'd convert to some form of linux but never quite having a good enough reason to. That changed when I stumbled upon UbuntuStudio and I started brainstorming options..

I want to run this system on my computers at school booting from an external drive (I know this wouldn't work well, but it would have to do until I can convince IT guys to allow me to partition a drive or some other more permanent fix((maybe you guys have suggestions?)). I would like for its desktop environment to be clean and user friendly - only 3maybe4 icons (depending on what apps i'll be including) and the desktop would be an image with my school name all pretty and a short paragraph next to each icon for the computer newbies that would be using it.

So basically here's what i need help with:

Choosing a distribution that suits my needs (I'm starting with ubuntustudio but i'm so completely new to alternative OSes like this that i don't even really know my options.

Partitioning the external drive appropriately to boot on startup.. any suggestions here would be great - is it worth me buying a firewire drive and would i have to do anything different setting up hardware options? what's a swap file and how can i make my files work in both XP and whatever distro i'm using.

Choosing a desktop environment that suits my needs - I want everything about it to be geared for multimedia production. I don't want kids who don't know any better going into system settings looking for pron

Any suggestions on software-since i don't know better-would be great!

Thanks in advance - I hate to dump all this on someone else (i usually just work things through trial and error style) but its hard to find an all inclusive resource for this kind of thing except in the collective consciousness of a forum

---

### Post by strabes on 2007-10-07
> **manichean said:**
> what's a swap file and how can i make my files work in both XP and whatever distro i'm using.

A swap file is similar to a paging file in windows. It is used when your physical RAM gets filled up and when hibernating.

You have several options for reading & writing files in both XP and linux, depending on where you are storing the files. Most external hard drives come formatted as FAT32. This works in both windows and linux but cannot store files greater than 4gb (I think that is the number).
If you're storing them (music, documents, etc) on a separate partition, which is what I do, you could partition the (external) drive as ext3 and then use the driver from fs-driver.org to read and write to ext3 in XP.
You could (although I don't recommend it) make the drive NTFS and then read/write to it in linux using ntfs-3g.

Hope this helps

---

