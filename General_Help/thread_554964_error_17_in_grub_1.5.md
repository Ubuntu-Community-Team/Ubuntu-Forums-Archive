---
title: "error 17 in grub 1.5"
date: 2007-09-19
forum: General Help
---

### Post by geoffLW on 2007-09-19
Hi

I guess that theres some kind of corruption of file systems ...  but I'm not entirely sure.
Can someone please either point me in the right direction to find out what this error IS. OR , tell me how to fix this problem from a CD installation, perhaps?
I see from other posts that there are / is / has been  life after version 1.5 of GRUB. Was there a good reason for this? [or did someone get very bored].

thanks in anticipation..
geoff

---

### Post by por100pre1 on 2007-09-19
[Here]("http://www.gnu.org/software/grub/manual/html_node/") you can read about that error:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

EDIT: Try using a LiveCD to mount the partition to check if it is ok,. You can try reinstalling GRUB with Super GRUB Disk

---

### Post by geoffLW on 2007-09-19
Many thanks.. that all makes sense now.. though I'm still trying to figure out why things went 'pear-shaped'.
geoff

---

