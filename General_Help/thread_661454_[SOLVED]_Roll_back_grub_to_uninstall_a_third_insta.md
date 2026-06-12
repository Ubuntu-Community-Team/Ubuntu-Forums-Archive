---
title: "[SOLVED] Roll back grub to uninstall a third instance of ubuntu?"
date: 2008-01-07
forum: General Help
---

### Post by phatty420 on 2008-01-07
Hello.

I am basically trying to uninstall my third OS.  I know that I can completely delete the partition, however I know that grub is loading from the third one as that is the most recently installed OS.  

A quick summary of what I did: I installed Winxp on a fresh hard drive, then I installed Ubuntu 7.10 (desktop).  Then after that I installed Ubuntu server.

Now I'm pretty sure that grub is loading from the Ubuntu server edition, and that's the OS (and partition) that I want to get rid of.  Here is how the operating systems are setup:

/dev/sda1 - WinXP
/dev/sda2 - Ubuntu (main OS)
/dev/sda3 - swap
/devsda4 - extended 
/dev/sda5 - ubuntu server
/dev/sda6 - swap

I would like to get rid of everything from sda4 and add that space to sda2 if possible.  Any help would be much appreciated.  Please let me know if there is any other that can help you help me.

---

### Post by p_quarles on 2008-01-07
Sure you can delete the server partition. You'll need to reinstall GRUB on a different partition after doing so, but that's relatively easy:
**[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)**

---

### Post by phatty420 on 2008-01-08
yes that worked great!  I just followed the instructions without the live cd and it worked perfectly!  Thank you very much for your help.

---

