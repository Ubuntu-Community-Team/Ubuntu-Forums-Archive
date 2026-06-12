---
title: "EXT4 missed/corrupted files after clean shutdown."
date: 2012-10-29
forum: General Help
---

### Post by vsespb on 2012-10-29
Hello.

I have shutdown problem (discussed in another thread) [http://ubuntuforums.org/showthread.php?t=2077756&goto=newpost](http://ubuntuforums.org/showthread.php?t=2077756&goto=newpost)

so,

1. Shutdown does not complete ( I had to turn box off manually )

2. BUT I have a log line in syslog: "kernel: Kernel logging (proc) stopped." That does mean that shutdown was clean. And, at least, disks are synced and perhaps filesystem unmounted. and shutdown failed already after sync/unmount.

3. After first fail, when I booted and all my firefox settings was destroyed, Skype and Rubymine were OK. After second fail my RubyMine settings were destroyed (and reporting that some setting file is empty), my Skype was still ok. After third fail my skype was reset. so I assume I have corrupted missed files here.

4. I rebooted to recovery mode, unmounted /home and ran fsck /dev/sdx - all OK, no errors.

so, how could this (1,2,3,4) happen together? ( want to discuss this without touching the reason of shutdown failures)

p.s.
hardware, memory etc was ok when I last checked.

---

### Post by vsespb on 2012-10-30
I am thinking now this  can be upstart problem - some service, which use /home partition, is not stopped when it's unmounted.

There can be bugs with upstart scripts.

For example his bug affects me for sure (however it's not related to shutdown)
[https://bugs.launchpad.net/ubuntu/+source/squid/+bug/831628](https://bugs.launchpad.net/ubuntu/+source/squid/+bug/831628)

This bug does not affect me [https://bugs.launchpad.net/ubuntu/+source/squid/+bug/750371](https://bugs.launchpad.net/ubuntu/+source/squid/+bug/750371)

So I am thinking now of a best way to debug shutdown/unmount process to find other possible upstart problems ?

---

### Post by dino99 on 2012-10-30
remove "spash" from /etc/default/grub, then run "sudo update-grub" to get a verbose shutdown mode that let you know when/where the problem is.

---

