---
title: "Can't boot into Gutsy anymore after kernal updates"
date: 2007-12-29
forum: General Help
---

### Post by jarmenia on 2007-12-29
I installed the updates that were pushed to my desktop yesterday and today when I started the machine first I'd get a fatal 15: file not found.  I did some research and found this thread:  [http://ubuntuforums.org/showthread.php?t=543943](http://ubuntuforums.org/showthread.php?t=543943)


So when I edit grub to boot off of (hd1,0) I get passed that error but instead when Ubuntu starts to load, I get the ubuntu flash screen and then I get dumped to BusyBox.  I did some more research and found this thread [http://ubuntuforums.org/showthread.php?t=295508](http://ubuntuforums.org/showthread.php?t=295508) and followed the instructions to do a minimal install with still no luck.  Can someone give me a hand as I'm pretty new to linux.

thanks,

John

---

### Post by jarmenia on 2007-12-29
Whew, figured it out.  What happened is that not only was the entry in my menu.lst incorrect in terms of the root (it said hd0,1 when in fact it should have been hd1,0) but the UUID in the menu.lst was also pointing to the wrong hard drive.  Once I changed that to the correct UUID as well it booted fine.

---

### Post by meierfra on 2007-12-29
To avoid this problem after the next kernel update you  need to fix  the 

#groot  .....

and

# kopt=root=UUID= ....

lines in menu.lst

---

### Post by jarmenia on 2007-12-29
great.  Thanks for the tip.  I was dreading the next kernal update.

---

