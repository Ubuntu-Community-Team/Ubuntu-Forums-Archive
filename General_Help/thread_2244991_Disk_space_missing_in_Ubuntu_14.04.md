---
title: "Disk space missing in Ubuntu 14.04"
date: 2014-09-20
forum: General Help
---

### Post by tm1729 on 2014-09-20
After updating from Ubuntu 12.04 to 14.04 the properties of all mounted drives shows an unknown portion. 
The used space and free space doesnt add upto total space. What's going on?
Here is a snapshot.

[ATTACH=CONFIG]256557[/ATTACH]

Thanks for helping

---

### Post by grahammechanical on 2014-09-20
I am seeing the same effect and I am using Utoptic Unicorn where File Manager (Nautilus) is at version 3.10.1. So, there is nothing wrong with your system. This is happening because a) it is the way the Gnome developers designed Nautilus to be. b) The Gnome developers have more work to do to complete the implementation of their designs. c) It is a bug.

Regards.

---

### Post by Impavidus on 2014-09-20
5% reserved space?

---

### Post by mcduck on 2014-09-20
Yeah, I'd agree with previous posts, it's a combination of the Ext4 filesystem's reserved space, and some of the files & directories being owned by root so Nautilus ran as a normal user can't access them, plus of course the normal filesystem overhead together reducing the space that is available to normal users.

---

