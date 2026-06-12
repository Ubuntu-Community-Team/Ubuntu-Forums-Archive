---
title: "[SOLVED] Command Line Capitals"
date: 2007-10-05
forum: General Help
---

### Post by El Rogueo on 2007-10-05
I just recently installed Xubuntu 7.04 on a really old computer (300MHz, 128MB of RAM) from the alternate installation CD, and I installed it as a command line system, something I've never done before.

When it boots up it hangs on the "starting boot scripts" message, at which I press enter, am told my login is incorrect, at which point a prompt comes where I can actually login.

The weird thing is, after I press enter everything is in caps. Everything I type, everything I see, is in caps. Caps lock and shift do not change this, but there must be a difference. For example

```
ANON@ANONMACHINA:/HOME$ LS
-BASH: LS: COMMAND NOT FOUND
ANON@ANONMACHINEA/HOME:~$ LS
ANON
```

where the first time I type "LS" and the second time I type "ls"

on an added note, my user account is called "anon" for the purpose of this example, and my computer "anonmachinea", both of which appear in all capital letters

so input is still case-sensitive, but I just can't see it...:(

any ideas?

---

### Post by alan.clements on 2007-10-05
I had a similar problem with a kubuntu CD I burned. As it turned out when I MD5'd the data on the CD and compared it with the original they of course didn't match which means the disk was corrupted. 

So I would suggest that you start there. Second possibility is the hard drive may be failing.

---

### Post by El Rogueo on 2007-10-05
> **alan.clements said:**
> 
So I would suggest that you start there. Second possibility is the hard drive may be failing.

I burnt the CD from my other machine, which is running Xubuntu successfully, and I burnt it with K3B which checks the MD5sum before it burns if you wait a few seconds, so it's not the CD I don't think. I've also used it for other successful installs.

Can you elaborate on the hard drive failure?

thanks for the quick reply

---

### Post by alan.clements on 2007-10-05
hard drives like floppy drives and cassette tapes use a magnetic surface to hold the data. Unfortunately the surface deteriorates over time causing bad blocks of data. When writing to blocks which are on the verge of failing it is possible that the data could be corrupted on formating. You did not say that the problem is intermittent so we could assume that the memory is not bad. 

Just to be sure run memtest just to be sure. 

Secondly try ```
md5sum /dev/cdrom
``` on the CD-ROM you burned from the machine your having problems with. If  'md5sum' is not corrupted you will be able to confirm that the machine is reading the disc correctly.

if all goes well so far, you can try using 'badblocks(8)' from a live CD. If that shows no problems.
I would suggest a reinstall. It's not impossible that you had a minor power flicker caused a problem.

I've installed various flavors of ubuntu, including Xubuntu and have had similar problems but it always came down to a problem with the CD media or the Hard drive media.

and yet another option if the drive supports S.M.A.R.T. technology

while SMART isn't always perfect it will give you an idea if your having a problem.

Read more here: [http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html]("http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html")

---

### Post by El Rogueo on 2007-10-06
Thanks much. In all the times I've installed (x)ubuntu I've never had this problem before.

Turns out it was just the tty being strange. When I switched to tty2,3,4,etc the problem wasn't there, so I just exited and logged back in and it was gone.

Strange but it's good now.

Thanks for the help though, it did help me identify some bad drives full of corrupted blocks.

---

