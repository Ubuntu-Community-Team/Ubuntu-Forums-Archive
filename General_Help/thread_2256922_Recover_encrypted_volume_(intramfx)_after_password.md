---
title: "Recover encrypted volume (intramfx) after password"
date: 2014-12-15
forum: General Help
---

### Post by easy2 on 2014-12-15
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][FONT=Verdana]After running apt-get update/upgrade the following morning I could not use the operating system to do much of anything. I kept getting notifications that it was mounted as read only. [/FONT]I rebooted and I’m brought to the following after entering the password:
 
[mount: mounting /dev /root/dev failed: no such file or directory]
[mount: mounting /dev /root/sys failed: no such file or directory]
[mount: mounting /dev /root/proc failed: no such file or directory]
[Target filesystem doesn't have /sbin/init.]
[No init found. Try passing init= bootarg]
 
(initramfs) 
 
In Gparged I have:
 
/dev/sda1 FS: ext 2
 
and 
 
/dev/sda2 FS: extended
--- /dev/sda5 FS crypt-luks
 
 
 
I’ve tried the combinations listed online. I think it has to do with working with an encrypted volume. Any help would be aprechiated.

---

### Post by oldfred on 2014-12-16
It sounds like update did not complete.

And many users with full drive encryption do not houseclean old kernels and the /boot partition fills so updates then do not work. There are many threads on the issue of full /boot partitions.

Boot the live installer version and from terminal post this:
df -h

Mount encrypted partition
[http://ubuntuforums.org/showthread.php?t=2198594](http://ubuntuforums.org/showthread.php?t=2198594)
Other /boot issues
[http://ubuntuforums.org/showthread.php?t=1632033](http://ubuntuforums.org/showthread.php?t=1632033)
[http://ubuntuforums.org/showthread.php?t=2242089](http://ubuntuforums.org/showthread.php?t=2242089)
[http://ubuntuforums.org/showthread.php?t=2239126](http://ubuntuforums.org/showthread.php?t=2239126)
[http://ubuntuforums.org/showthread.php?t=2235403](http://ubuntuforums.org/showthread.php?t=2235403)

---

