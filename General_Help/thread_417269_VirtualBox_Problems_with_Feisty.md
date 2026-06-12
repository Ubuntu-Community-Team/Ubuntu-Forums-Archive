---
title: "VirtualBox Problems with Feisty"
date: 2007-04-21
forum: General Help
---

### Post by rabideau on 2007-04-21
Anyone have any success figuring out how to:

1. Get the usb to work in WinXP client of VirtualBox 
2. Network and/or drive shares between the WinXP client and Ubuntu host?


ps.
I have my installation process for VirtualBox posted at:
[http://ubuntuforums.org/search.php?searchid=18450670](http://ubuntuforums.org/search.php?searchid=18450670)

---

### Post by scotttkd on 2007-04-21
I am having problems with the file sharing as well.  I saw some instructions on the virtualbox website about running vboxmanage in the xp installation, but I cant find that .exe in my virtualbox install.

---

### Post by rabideau on 2007-04-21
Just  open a terminal window on your ubuntu machine and enter VBoxManager at the prompt.  All the commands are there but... I still can't get it to work eve with the terminal and command lebel prompt.   I'm certain there are some settings within Linux that I have wrong.  But being new to Linux, I have no idea what they might be.:(

---

### Post by rabideau on 2007-04-22
The fix for my USB problem was provided by Bodhi at:

[http://ubuntuforums.org/showthread.php?p=2507870#post2507870:guitar:](http://ubuntuforums.org/showthread.php?p=2507870#post2507870:guitar:) 

Thanks!

I'm down to one problem with VirtualBox now!!! Hooray.  _**Anyone solved the problem of Networking and/or drive shares with VirtualBox???**_

---

### Post by rabideau on 2007-04-29
Not that many people appear to be reading this thread but I have fixed one of my problems.

Sharing the disks between Ubuntu (host) and XP (guest) requires two critical items.

[LIST=1]
[*]Using VBoxManage be certain to identify a share (obvious I know).
[*]Open the Guest OS in VirtualBox and at the windows command prompt enter the net use string per instructions in VBoxManage; be certain to use an UNUSED drive letter (that's where my problem was).
[/LIST]

Good luck!

---

### Post by scotttkd on 2007-05-01
i was following this thread in hopes of making virtualbox work the way I wanted and then I found a link from bodhi in another thread that fixed everything.  awsome link and shold be in the online help manual in virtualbox!


[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

