---
title: "Add to startup as root?: zfs mount -a"
date: 2013-04-14
forum: General Help
---

### Post by Alvinator9000 on 2013-04-14
Hello everyone, I'm pretty new to Ubuntu, but I've got now a 6 drive Raidz1 array based on 3TB drives, and unfortunately I've messed up my ZFS install so now it doesn't auto mount things on startup.  I was wondering if anyone else is having this issue and if anyone would be able to point me in the right path to figuring this out, I'd basically like the system to boot up (Gui) then run the "zfs mount -a" but it has to be run as root whilst I'm logged in as anything else.  

I know its not about having all the answers but its all about asking the right questions, and my question may not seem the greatest or be that clear so please don't hesitate to ask me to clarify anything and I will do my best to do so!!

Thank you all in advance for your help and/or responses!! :)


PS, running Ubuntu-Studio, not that this should matter all that much, and running zfs-ubuntu from the native/stable arm of the Zfs on Linux ppa.


Tags: ZFS Mount -a, ZFS Auto Mount, ZFS Auto-mount, zpool auto mount (Apparently I couldn't "create" tags...)

---

### Post by TheFu on 2013-04-14
Doesn't ZFS mount using the /etc/fstab just like any other file system?
Or are you running a FUSE-zfs?

---

### Post by Alvinator9000 on 2013-04-16
WOW, I just had a HUGE long message I was hoping to post but when I clicked "Post quick reply" my "token has expired" :/

Anyways, here is where I got my ZFS from: [http://zfsonlinux.org/faq.html](http://zfsonlinux.org/faq.html)

On it shows this: 
> [TABLE="width: 80%"]
[TR="bgcolor: #aaaaaa"]
[TH]1.14 How do I automatically mount ZFS file systems during startup?[/TH]
[/TR]
[TR]
[TD]
[LIST]
[*]**Ubuntu PPA:** Auto mounting is provided by the enhanced mountall package from the [ZFS PPA]("https://launchpad.net/~zfs-native/+archive/stable"). Install the ubuntu-zfs package to get this feature.
[*]**Fedora, RHEL, Arch, Gentoo, Lunar:** Init scripts for these distributions have been provided. If your distribution of choice isn't represented please submit an init script modeled on one of these so we can include it.
[/LIST]
[/TD]
[/TR]
[/TABLE]


I think this problem is tied to my 10 minute boot time (which I'd like to bring back down to 32 seconds or so), I didn't JUST install ubuntu-zfs, I installed the zfs-native/stable ppa, then searched package manager for 'zfs' and installed nearly everything I could, that would probably do it :P  

I think I'll reinstall but I'd at least like to get to the root of the problem before I do so, so that way the next guy who has the same problem doesn't come looking at this thread thinking its solved only to find out I just reinstalled and didn't actually solve anything but instead just avoided it :P

Thanks for your patients and your time, if there's anything else you'd like me to look for please let me know :)  I'll be reinstalling in a few days IF I end up needing to

---

