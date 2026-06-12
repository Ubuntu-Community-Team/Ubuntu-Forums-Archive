---
title: "New Ubuntu + Sony VAIO user: Many ?s"
date: 2007-12-22
forum: General Help
---

### Post by Wan_Lin on 2007-12-22
Hi!

I am a new Ubuntu user who is trying to get an installation settled so I can start delving deeper into Ubuntu itself.

I have a Sony VAIO VGN-FJ170, with a 100GB HD and 2GB ram... blah blah blah.

Anyway, I'll post my situation and hopefully someone will be able to guide me into a good direction to start in.

I have been using Windows my whole life. I am a computer science major, so I wanted to start using Ubuntu firstly because I like the appeal of linux and especially Ubuntu and secondly for the programming aspects of it. I have successfully installed a hasty dual boot of Ubuntu and Windows XP. However I am not satisfied... here are my issues:

MAIN ISSUE: If this is solved it will circumvent the other issues completely. I only want Windows to run certain things I don't feel will run in Ubuntu. Namely, iTunes (and using my iPod), and a Harry Potter computer game my girlfriend likes. I have tried Wine to run Harry Potter, which didn't work. I have also tried to get VirtualBox working to run Windows within Ubuntu, but that didn't work because the ISO for my XP disc (a burned copy of a student edition) didn't work, I think. It just didn't work, however it may be because of the ISO or other things. If there are ways to use my iPod with Ubuntu, and also a way to run Harry Potter on Ubuntu, I would much prefer a single boot of Ubuntu over a dual boot. Ideas?

SECONDARY ISSUE: I am not sure my dual boot partitioning was done correctly. I have 4 partitions: 1 for Windows XP, one for Ubuntu, one for swap, and another partition that I am not sure what it is for, but I don't feel comfortable formatting it for that reason. It is a 6GB partition of (looking in the drive) drivers, "Sony" stuff, volume info, art, docs, etc. The issue is that the drive (called "sda1") shows up on my desktop and I cannot unmount it. It is annoying to look at. I do not know what this partition is for, and why it is on my desktop. Do I need this partition? If so, is there a way to remove the icon from the desktop?

Other issues:
-On GRUB I have 5 choices for OS's: Ubuntu, Ubuntu safe mode, Ubuntu RAM check, Windows XP Professional, and Windows NT/2000/XP. Why do I have these many, and how can I change this?
-My Windows boot runs slowly (slower than Windows runs, say, when you first install it. This is not because of Ubuntu, however). I want to reformat it with a new copy of windows, is this possible to do just in the partition I have alloted for it?

I am perfectly okay with reinstalling Windows/Ubuntu or whatever needs to be done, as long as I know that's the right thing to do for what I want.

Any help that can be given will be greatly appreciated! I really want to use Ubuntu! Thanks in advance!

---

### Post by irwa82 on 2007-12-22
Hi,

For the harry potter game transgamings cedega seems to have some support:

[http://games.cedega.com/gamesdb/games/alphabrowse.mhtml?letter=H](http://games.cedega.com/gamesdb/games/alphabrowse.mhtml?letter=H)

as for the ipod I don't have one but the following may be what you want:

[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

the grub file with the menu setting is here  /boot/grub/menu.lst

reinstalling windows will wipe the boot sector making grub not work any more with a linux boot disk you can rewrite grub into the boot sector.

before reinstalling any os you should make sure you have all your important data backed up.

I have not read this article but it may help you:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Anyway hope this helps you out.

---

### Post by Wan_Lin on 2007-12-22
I prefer not to use Cedega since that is proprietary and I feel this problem can be solved with no money involved.

After I posted the topic I remembered that I would also like my digital camera (Sony) to work too... dunno if there is some support for cameras. But I will take what I can get as this goes on...

---

