---
title: "Ubuntu will not boot after Fedora 9 Install"
date: 2008-05-23
forum: General Help
---

### Post by WaddleDee on 2008-05-23
Hello

I recently installed fedora 9 on a partition, and tried booting into Ubuntu Hardy, but it did not work. I don't want to wipe my ubuntu. Please help!

---

### Post by Monicker on 2008-05-23
What happens when you try to boot into Ubuntu?  Is it possible that you installed Fedora over the Ubuntu partition?

---

### Post by WaddleDee on 2008-05-23
No, it is not over written. Even from the Fedora I can mount and browse the ubuntu partition. :)

When I try to boot it doesn't do anything, it says some stuff (bogus boot parameters) and errors and returnes to the menu...

Am I asposed to set some sort of boot parameters??? Would that help?

---

### Post by WaddleDee on 2008-05-23
I know I am not asposed to spam with posts, but I am in an Ubuntu Emergincy. I need my Ubuntu back. Could the community plz just pay a lil attention?
I have a ton of work I need to do

Please

---

### Post by WaddleDee on 2008-05-23
Ohh, um just a little update
In my /boot/grub/menu.lst It put Ubuntu as this:

```
title Ubuntu 8.04 Hardy Haron
	rootnoverify (hd0,1)
	chainloader +1

```

Does that help?

---

### Post by kpkeerthi on 2008-05-23
It looks like you installed fedora's grub to MBR and it overwrote ubuntu's grub. 

That command above will not work unless ubuntu's grub is installed in (hd0, 1) which could be /dev/hda2 or /dev/sda2 in your case. 

Are you sure ubuntu's grub is available at the location fedora is pointing to. /dev/hda2 or /dev/sda2 that is?

---

### Post by kpkeerthi on 2008-05-23
Follow this thread and **install ubuntu's grub to the partion (not MBR)** that fedora is looking for. Once setup, fedora's grub chainloads ubuntu's and this preferred. See why [here]("http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html")

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
(There is a note at the middle of the post on how install grub on to a partition).

---

### Post by buntunub on 2008-05-23
I learned my lesson about Fedora back at Core 6 when I installed that on a spare partition and it destroyed both my Windows AND my Gentoo install. I was VERY upset to say the least! Needless to say, it is not wise to install Fedora without first exhaustively testing it on a virtual machine (Virtual Box is my personal favorite), and even then, never install it until at least a full month post release. Fedora 8 is quite nice now, but it took quite some time to get it there. Nothing wrong with this from Fedora's perspective, as it is NOT a distro for newbys like Ubuntu.

Several things you can do to recover your GRUB. Fix it from Fedora boot, or fix it from the Ubuntu Livecd. Many guides abound about how to do this. Most the time, just fixing your menu.lst does the trick, but with Fedora (which is thus far the only distro to have ever completely destroyed all my installs), thats a crap shoot. Sorry, but I guess im still a bit miffed at losing my Gentoo install. It only took me about 5 days to get that just right and then BOOOOM!

---

### Post by WaddleDee on 2008-05-24
Dude, Thanks buntunub! I used the Ubuntu live cd and set my Ubuntu partition as the root partiton in grub, and then rebuilt the MBR.

After that, I wiped the Fedora 9 partition. :)

[solved]

---

