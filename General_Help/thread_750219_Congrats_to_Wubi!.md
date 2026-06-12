---
title: "Congrats to Wubi!"
date: 2008-04-09
forum: General Help
---

### Post by Vadi on 2008-04-09
[News story!]("http://blogs.zdnet.com/hardware/?p=1570") Very well deserved for your efforts imo. Congrats 

I was wondering though, the same thing as this comment ([click]("http://talkback.zdnet.com/5208-12554-0.html;jsessionid=7XR-Fja8VX6dFavZKr?forumID=1&threadID=45874&messageID=855594&start=-9838")). Is there an easy guide to go about doing that?

---

### Post by ago on 2008-04-09
Thanks

"Now I want to eliminate Windows of off my system. Is there a way that I can do this without having to reinstall the distro again and have to go through all the hardware setups again?" 

Now we have to do it in a 3 step process. 

1) Free a partition with whatever partitioning tool you want, 
2) move Wubi installation to that partition using LVPM or similar, 
3) remove the old Window partition and (optionally) extend the Linux partition. 

There are some techical issues to do that in one step from within a running Wubi installation, which we will probably work on in the next release cycle. It is also likely that the CD installer will be able to detect existing wubi installations and offer to migrate them to a dedicated partition as one of the installation options. That will take care of 1-2-3 but will require a physical CD. 

In particular, step 2 above is not that complex, it literally requires dumping the files from the virtual disk to a real partition, install grub, and modify fstab and menu.lst. Other than fstab/menu.lst a wubi installation is in fact identical to a normal installation since all the old code has been incorporated within Ubuntu. I would expect an advanced user to be able to do it manually without too much trouble. Of course there is also LVPM to ease the pain.


That of course requires free space  = 2X wubi installation size (1X for the version already installed, 1X for the version to be installed).

---

### Post by Vadi on 2008-04-09
Hopefully the migration tool will be finished for 8.10 or something then :)

---

### Post by Crafty Kisses on 2008-04-09
> **Vadi said:**
> [News story!]("http://blogs.zdnet.com/hardware/?p=1570") Very well deserved for your efforts imo. Congrats 

I was wondering though, the same thing as this comment ([click]("http://talkback.zdnet.com/5208-12554-0.html;jsessionid=7XR-Fja8VX6dFavZKr?forumID=1&threadID=45874&messageID=855594&start=-9838")). Is there an easy guide to go about doing that?

Congrats Wubi!

---

### Post by w3stfa11 on 2008-04-09
> **ago said:**
> Thanks

"Now I want to eliminate Windows of off my system. Is there a way that I can do this without having to reinstall the distro again and have to go through all the hardware setups again?" 

Now we have to do it in a 3 step process. 

1) Free a partition with whatever partitioning tool you want, 
2) move Wubi installation to that partition using LVPM or similar, 
3) remove the old Window partition and (optionally) extend the Linux partition. 

There are some techical issues to do that in one step from within a running Wubi installation, which we will probably work on in the next release cycle. It is also likely that the CD installer will be able to detect existing wubi installations and offer to migrate them to a dedicated partition as one of the installation options. That will take care of 1-2-3 but will require a physical CD. 


Can't wait to see the improvements in the next Wubi (8.10) release. Wubi really is a fantastic tool.

---

