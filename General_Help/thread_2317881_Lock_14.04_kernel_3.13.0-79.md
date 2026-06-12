---
title: "Lock 14.04 kernel 3.13.0-79"
date: 2016-03-20
forum: General Help
---

### Post by jbdough on 2016-03-20
can we *chat* about where I might go for support?

I ***need*** to be stuck on 3.13.0-79

I got this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559288](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559288)

and this too
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/1558128](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/1558128)

How do I wait out a dist-upgrade until it is going to work?

---

### Post by Bucky Ball on 2016-03-20
*Post moved to own thread.*

You would post in a support area for support. :)

Better here. You posted on a non-support thread in a non-support forum area. This is support so better here. It will improve your chances of support.

You can lock on to the kernel you have, ignoring others during update as far as I know. Don't know how, but others will and hopefully will jump in and help shortly. 

Good luck.

PS: You can change your thread title by editing the first post, Go Advanced. ;)

---

### Post by jbdough on 2016-03-20
thanks Bucky

I appreciate and believe the thread topic is as good as any I could present.

---

### Post by deadflowr on 2016-03-20
Is [lpbug]1559288[/lpbug] your bug?
If so, you need to run
```
apport-collect 1559288
```
so that the log files make it into your report, and then mark the report as confirmed,
as pointed out by the Brad Figg post.
(or, as pointed out by the post, if you cannot run the command, comment on it in a post and then confirm)

If it is not your report, then you should mark it as affects me too.

The second bug report is a dupe of this: [lpbug]1558114[/lpbug]
of which a fix was released.
(Did the fix not work, for you?)


But going beyond that, to how to keep the bootloader on one kernel forever:
[http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry](http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry)
I think this gives you what you want.
It is one method you can try.

Another method is to create a simply custom file for grub:
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
this scenerio requires more work, since you'd also need to move the file around
(you'd want to move to something like 09_custom in the /etc/grub.d folder, so it's entry is read before the main linux entry is read, which would place the entry first in the boot menu, and then default to it, if need be.)

The first method is pretty simple, so I'd recommend that.

---

### Post by jbdough on 2016-03-21
thanks flowr - that is useful information.

numero uno:  not my original bug, nope.  I almost get through logging in then stuck at the Xubuntu desktop with a frozen mouse and no keyboard with 83
number 2: didn't get fixed for me.

I'd like to be able to know when I could resume dist-upgrades if I did keep the bootloader on 79 for awhile.

---

### Post by deadflowr on 2016-03-21
> [COLOR=#000000]I'd like to be able to know when I could resume dist-upgrades if I did keep the bootloader on 79 for awhile.[/COLOR]

Nothing's stopping you from installing updates.

---

### Post by mastablasta on 2016-03-22
in synaptic one can lock packages. I am not sure if kernel can also be locked.

---

### Post by jbdough on 2016-03-28
Thanks to all for helpful suggestions.

All things come to those who wait.  Just thought I'd try apt-get update && apt-get upgrade one more time - 
and am happy to report success from the functioning kernel upgrade.

It seems the libpam-modules bug cleared up and now can boot 3.13.0-83

---

