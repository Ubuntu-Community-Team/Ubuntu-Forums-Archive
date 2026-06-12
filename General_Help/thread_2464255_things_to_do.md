---
title: "things to do"
date: 2021-06-27
forum: General Help
---

### Post by jgw on 2021-06-27
I am looking for a list of things that should be done to fix and cleanup a system.  Here is my existing list but I suspect it really needs updating.
sudo apt update           ##syncs the data bases between your system and your mirror site
sudo apt upgrade         ## updates installed software to what is current on your mirror
sudo apt -f install         ## looks and tries to 'fix' broken packages
sudo dpkg -C               ## runs an 'audit' of the package management system
sudo apt autoremove
apt --fix-broken install

fsck - unmount drive before running ([https://phoenixnap.com/kb/fsck-command-linux):](https://phoenixnap.com/kb/fsck-command-linux):)
sudo umount /dev/sdb				Unmount drive
sudo fsck -y /dev/sdb				Fix Detected Errors Automatically with fsck
sudo fsck -n /dev/sdb				Skip Repair but Print fsck Errors in the Output
sudo fsck /dev/sdb					Run fsck to Check for Errors
sudo fsck -f /dev/sdb				        Do a file system check
sudo fsck -AR						Run fsck on All Filesystems at Once (skipping root drive)
sudo fsck -AR -t noext3 -y			        Skip fsck on a Specific Filesystem
sudo fsck -M /dev/sdb				Skip Fsck on Mounted Filesystems

---

### Post by GhX6GZMB on 2021-06-27
And the question is?

---

### Post by scorp123 on 2021-06-27
This isn't Windows. Unless you really have a specific problem then I'd dare say you don't need to run those commands.

**Don't try to "fix" something if it isn't even broken in the first place.**

The most "clean up" I ever do apart from making sure my patches are up do date is to move away or even to outright delete all the compressed old log files from **/var/log**:  all the ***.gz** files there can begin to take quite some space on a very active system (e.g. a server that's being used by 100's of people daily). But other than that? Nope. No need.

---

### Post by dddman on 2021-06-27
I don't know scorp123, I think clean the stuffings out of it.  And that's why I like Bleachbit because of its likeness to Crap Cleaner (CC cleaner?), it goes way beyond autoremove/autoclean (which is included).

sudo apt install bleachbit

---

### Post by scorp123 on 2021-06-27
> **dddman said:**
>  I think clean the stuffings out of it.
Such as??

> **dddman said:**
>  
sudo apt install bleachbit 

This software doesn't do anything I can't do myself. But I can see the appeal for new users.

---

### Post by dddman on 2021-06-27
> **scorp123 said:**
> Such as??  This software doesn't do anything I can't do myself.
It's all bundled in one convenient package.
[https://www.bleachbit.org/features](https://www.bleachbit.org/features)

---

### Post by wildmanne39 on 2021-06-27
With bleachbit you have to be careful, every time I have used it it always removes needed files and I have seen many threads about this same issue over the years, I personally do not recommend using it, of course I have not used it in a long time but at least use caution.

---

### Post by dragonfly41 on 2021-06-27
Stacer (GUI) is also useful.

[https://oguzhaninan.github.io/Stacer-Web/](https://oguzhaninan.github.io/Stacer-Web/)

---

### Post by dddman on 2021-06-27
> **wildmanne39 said:**
> With bleachbit you have to be careful, every time I have used it it always removes needed files and I have seen many threads about this same issue over the years, I personally do not recommend using it, of course I have not used it in a long time but at least use caution.
Didn't know that.  Haven't had any problems, maybe it's the first setup that's gets people.

---

### Post by scorp123 on 2021-06-27
> **wildmanne39 said:**
> With bleachbit you have to be careful, every time I have used it it always removes needed files and I have seen many threads about this same issue over the years, I personally do not recommend using it, of course I have not used it in a long time but at least use caution.

That's my experience with such tools too, they sometimes end up removing too much. So I very much prefer dealing with any issues myself. And only if and when the need arises. Don't fix stuff if it isn't broken.

---

### Post by dddman on 2021-06-27
> **scorp123 said:**
> Don't fix stuff if it isn't broken.
I don't like a overstuffed couch :D

---

### Post by TheFu on 2021-06-27
Updated Ubuntu Desktop maintenance: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
Older version on a popular website: [https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282](https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282)

I'm not a fan of GUI tools. They lie and often don't do what the GUI implies they will do.
Also, be very careful scripting too many things without validating all prior commands completed successfully. This can get people into real problems.  In short, always check $? for a zero value after every command. If it is non-zero, stop!

---

### Post by jgw on 2021-06-28
Thanks for the replies.  There was a lot of stuff and I am gonna have to study on it.   thanks again!

---

