---
title: "rcS issues"
date: 2006-11-15
forum: General Help
---

### Post by 2eeks on 2006-11-15
So today when I went to boot my ubuntu desktop up it stopped about halfway through the startup and gave me an error.

The basic gist of it was:

init:Unable to execute /bin/sh for rcS: No such file or dir.
rcS process (1973) terminated with status 1
init:Unable to execute /bin/sh for rc-default: No such file or dir.
init: rc-default process (1974) terminated with status 1

Anyone know how to fix this? I have over 10gigs of music I just transferred to this install and I really dont want to lose it...

---

### Post by DavidTangye on 2006-11-15
My daughter rang me yesterday to tell me something similar. It started after running upgrades via Update Manager on Sunday. The machine was left to do this unattended, so would have selected default options if any came up: not a method I would recommend. The machine will not now startup at all. It fails during init. I will not get to see the machine for a few days though, so I cannot see the exact message and look into it til then. I just hope its not an upgrade of something then that has broken the system.

---

### Post by 2eeks on 2006-11-15
I was doing exactly that on sunday too! After running synaptic the system started acting up...

Anyone have any ideas for us?

---

### Post by DavidTangye on 2006-11-15
Well that makes me wonder if at that time there was either a release of some dud but key package, eg init itself, or it was placed into the pool some amount of time before a dependent package got there.

I do not know if the latter scenario is possible with debian repos: I certainly hope not. Can anyone confirm this?

---

### Post by 2eeks on 2006-11-26
Anyone have any helpful insight for this issue?

---

### Post by DavidTangye on 2006-11-26
I my case, the motherboard was beginning to fail. There seems to be nothing wrong with the repos.

---

### Post by erdalronahi on 2006-12-04
Boot from a Live CD and look whether /bin/sh links to bash or to dash. In my case it linked to dash which made the system unbootable.

---

### Post by 2eeks on 2006-12-04
How do I check this?

When I use the live CD, arent I just looking at the OS running in virtual memory?

How do I mount the hard drive installation?

ps. I ask this because I tried to use a sudo command and it asks me for a password, which I dont know...

---

### Post by erdalronahi on 2006-12-05
Open a terminal. Then:
mkdir /media/a
mount /dev/hda1 /media/a
cd /media/a/bin
ls -l sh

If it doesn't work try all these with "sudo". I never need a password, but it may be "ubuntu" or "livecd", I don't remember.

---

### Post by 2eeks on 2006-12-27
OK so I was able to mount the drive and found the files I've been trying to retrieve. Now Im stuck at trying to open the files... apparently the old copy of linux put owner only permissions on some of the files...

---

### Post by erdalronahi on 2006-12-27
If sudo worked once you can use sudo all the time. You could also try to change the permissions with sudo or copy the files and then open them.

---

