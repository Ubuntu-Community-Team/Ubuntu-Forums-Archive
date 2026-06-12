---
title: "Can't execute fsck"
date: 2013-05-26
forum: General Help
---

### Post by philled on 2013-05-26
I have a Mythbuntu virtual machine running on Citrix Xenserver. I had a power outage recently which has wreaked havoc and I've had to restore the VM from a backup. Now I can't mount a couple of the disks. I've unmounted the disks but when I try to run fsck I get this error:

[FONT=courier new]$ sudo fsck /dev/xvdb1
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Operation not permitted while trying to open /dev/xvdb1
You must have r/w access to the filesystem or be root[/FONT]

Well, I'm using sudo so surely I am root, so how come it's giving me this error? Is it something to do with it being a VM? Any ideas how I can get fsck to run?

---

### Post by claracc on 2013-05-26
Perhaps this thread can help you: [http://ubuntuforums.org/showthread.php?t=1508294](http://ubuntuforums.org/showthread.php?t=1508294)

---

### Post by philled on 2013-05-26
> **claracc said:**
> Perhaps this thread can help you: [http://ubuntuforums.org/showthread.php?t=1508294](http://ubuntuforums.org/showthread.php?t=1508294)

I booted the VM with a Ubuntu LiveCD and ran e2fsck on the offending disks and all was reported well. But when I reboot the machine proper I'm still getting reports of serious disk errors:

[FONT=courier new]Serious errors were found while checking the disk drive for /mnt/xvdb1.
Press I to ignore, S to skip mounting, or M for manual recovery
[/FONT]
And when I try to run e2fsck on them I get an error:

[FONT=courier new]root@mbe:~# e2fsck -f /dev/xvdb1
e2fsck 1.42 (29-Nov-2011)
e2fsck: Operation not permitted while trying to open /dev/xvdb1
You must have r/w access to the filesystem or be root[/FONT]

How come it doesn't report errors when I run e2fsck from the LiveCD but it does when I boot it up? And as I'm logged on as root why won't it let me run e2fsck? 

I've also found that I can actually mount the filesystem - but only in read only mode which isn't what I need:

[FONT=courier new]root@mbe:~# mount -a
mount: block device /dev/xvdb1 is write-protected, mounting read-only
[/FONT]

---

### Post by mrajdl on 2013-05-27
I'm sure I won't give you any answers, I'm an idiot at this Linux stuff, but the errors you get are the same I got went my HD started to fail.

I know it's no big help, but I'm just doing this to refresh the thread, holiday weekend, people gone visiting.

---

### Post by HiImTye on 2013-05-27
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are you trying to fsck a disk while it's mounted?

---

### Post by philled on 2013-05-28
I think I've found the solution to this. It turns out to be a Cixtrix  XenServer issue.

I removed the storage respositories from XenServer as per [CTX131328 - How to Remove a Storage Repository from XenServer - Citrix Knowledge Center]("http://support.citrix.com/article/CTX131328"). 

I then followed the instructions at [CTX121896 - How to Introduce a Local Storage Repository in XenServer - Citrix Knowledge Center]("http://support.citrix.com/article/CTX121896") to re-introduce the storage repositories. I reattached them to the Mythbuntu VM and it then booted up fine.

So definitley a XenServer issue, I think. Hope this helps someone else in the future.

---

### Post by claracc on 2013-05-28
Please, could you mark the thread as solved? [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

