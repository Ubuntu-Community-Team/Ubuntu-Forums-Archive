---
title: "Migrating to a new hard drive"
date: 2008-07-06
forum: General Help
---

### Post by chrisN_uk on 2008-07-06
I've recently installed a new hard drive and I'd like to move my Ubuntu installation onto it and use my current hd as a backup disk. I would also like to set up my new hd with a separate partition for /usr.

Question 1:
    Will setting up a partition for /usr as well as / and /home mean that when I upgrade/reinstall, my settings (gnome, compiz etc..) are preserved? If not, is this possible to do and which directories are needed?

Question 2:
   What is the best way of migrating to a new hard drive and splitting my file system onto multiple partitions?

I have tried to do this several ways and the best result so far is that I can boot from my new hd with all my files and programs available but with none (or al least only some) of my settings applied.  Every time I think I understand how to set up grub, MBR, and fstab, something bizarre happens and I realise I don't really get what's going on. 

Question 3: 
   Can you point me in the direction of a good book/website that gives an explanation of the linux directory organisation and what actually goes on when I turn my computer on?   


Thanks for reading this far...any help is much appreciated
Chris

---

### Post by logos34 on 2008-07-07
1. Yes.  (specifically, /usr/local).  Maybe /opt too (I know apps like picasa and adobe put stuff there)...gnome and other desktop settings are saved in /home (+ FF, email client, etc). 
Also, if you make a separate /var, your debs will be safe if you reinstall, and you won't have to re-download all of them.

2.  [Gparted 'copy/move']("http://gparted.sourceforge.net/larry/move/move.htm") function (the example in the link is ntfs, but the principle is the same for ext3).  Or [dd]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html") command.  Once everything is transferred, make [separate partitions for /home]("http://www.psychocats.net/ubuntu/separatehome") and other directories.

As long as you're using UUIDs in menu.lst and fstab, the only thing you should need to do is [install grub ]("http://ubuntuforums.org/showthread.php?t=224351")to the new drive's MBR.  That said, I've had problems getting email client to remember account settings, permission problems, etc. when transferring /home to separate partition. (even on same disk).  There is a gui tool called gnome-reset you might try to backup your settings/prefs

3. Look through the guides/howtos [here]("http://www.tldp.org/").

---

### Post by chrisN_uk on 2008-07-08
Thanks a lot, I'll give that a go when I have the chance.

---

