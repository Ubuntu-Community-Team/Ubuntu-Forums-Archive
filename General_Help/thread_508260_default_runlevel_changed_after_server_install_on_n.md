---
title: "default runlevel changed after server install on new partition"
date: 2007-07-24
forum: General Help
---

### Post by badrobot on 2007-07-24
i just installed ubuntu server 7.04 on a computer that has feisty desktop installed on a different partition.  during install, i was asked if i wanted to install grub again... installer recognized both my win and feisty desktop partitions - i said yes.  problem is this.  now, when i boot into feisty desktop, it defaults to what looks like rcS, the uibuntu splash screen gets about 1/4 of the way to the end, and i end up with root console.  if i do [FONT="Courier New"]init -v 2[/FONT] it says that it's stopping rcS and X and gnome start as usual.  I'd like it so that it booted into runlevel 2 from the getgo instead of staying in rcS.  

I looked into /boot/grub/menu.lst and compared between the server and the desktop, and couldn't figure out what to alter, if anything.  i also looked into /etc/event.d and the rc-default and again couldn't figure out what to do...  i'm a linux n00b, so i'm not quite up to analysing shell scripts yet, but it looked like the menu.lst and the rc-default scripts were almost the same between server and desktop.  

i hope this is clear enough an explanation of the problem.  any help is appreciated.

---

### Post by confused57 on 2007-07-24
> **badrobot said:**
> i just installed ubuntu server 7.04 on a computer that has feisty desktop installed on a different partition.  during install, i was asked if i wanted to install grub again... installer recognized both my win and feisty desktop partitions - i said yes.  problem is this.  now, when i boot into feisty desktop, it defaults to what looks like rcS, the uibuntu splash screen gets about 1/4 of the way to the end, and i end up with root console.  if i do [FONT="Courier New"]init -v 2[/FONT] it says that it's stopping rcS and X and gnome start as usual.  I'd like it so that it booted into runlevel 2 from the getgo instead of staying in rcS.  

I looked into /boot/grub/menu.lst and compared between the server and the desktop, and couldn't figure out what to alter, if anything.  i also looked into /etc/event.d and the rc-default and again couldn't figure out what to do...  i'm a linux n00b, so i'm not quite up to analysing shell scripts yet, but it looked like the menu.lst and the rc-default scripts were almost the same between server and desktop.  

i hope this is clear enough an explanation of the problem.  any help is appreciated.
I'm not sure what the problem is, but you could use the live cd to reinstall Feisty desktop's grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you could add a configfile entry to boot your server:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by badrobot on 2007-07-24
hey, thanks for replying.  i solved the problem.  although i actually misdiagnosed it at first.

i booted verbosely and saw that the fsck was having a problem resolving UUID=blahblahblah, it turned out that UUID=blahblahblah was the old UUID of the partition that i installed the server onto.  after installing the server, the UUID changed, but that change was not reflected in the feisty desktop fstab, so that when fstab went to mount that partition, it was using the old UUID.  so to fix it i just changed the old UUID for that partition to the new one in the fstab, and it booted normally  :guitar:

---

### Post by benx009 on 2007-07-24
yes, you have to be careful w/ UUID's, they can be really tricky...

---

### Post by badrobot on 2007-07-24
is there anything else i should be aware of with the UUID changing?  is it enough to just change the fstab?  or is there some other issue with the UUID lurking in my future?

---

### Post by benx009 on 2007-07-25
> **badrobot said:**
> is there anything else i should be aware of with the UUID changing?  is it enough to just change the fstab?  or is there some other issue with the UUID lurking in my future?

no not really.  just remember that if you ever format a partition on your hard disk, even w/ the same file system, the UUID will change.  also, if you have 2 or more linux distros booting up from your system, manage the UUIDs in /etc/fstab for **both** of them when you format a partition or install/reinstall another distro.  i think the command to check the uuid's of a partition in ubuntu goes something like: ```
:~#vol-id -u /dev/hdb1 
``` (that is just off the top of my head, i am not exactly sure, but that should be right).  notice that you must be root to do this.  

as long as you remember all that, you should be fine.  after all, you have much more in ubuntu to worry about right?;-)

btw, you can also configure your /etc/fstab to use the name of your partition (i.e. /dev/hdb1) rather than its uuid if it all gets a little too over your head

---

### Post by badrobot on 2007-07-25
thanks for the help.  i won't remember that command, but i can always search the forum ;)

and yes, learning linux has been challenging, or rather, time consuming :)
it's like an addiction, every solution to a problem is like a new high.  sometimes i think i like when stuff breaks, just so i have an excuse to fix it and learn a little more.

---

