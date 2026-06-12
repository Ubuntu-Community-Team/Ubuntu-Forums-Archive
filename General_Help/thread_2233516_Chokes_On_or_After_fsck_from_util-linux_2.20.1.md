---
title: "Chokes On or After fsck from util-linux 2.20.1"
date: 2014-07-09
forum: General Help
---

### Post by ctsstc on 2014-07-09
[http://askubuntu.com/questions/493431/chokes-on-or-after-fsck-from-util-linux-2-20-1](http://askubuntu.com/questions/493431/chokes-on-or-after-fsck-from-util-linux-2-20-1)

[COLOR=#333333]I have a box running at DigitalOcean with Ubuntu 12.04[/COLOR]
[COLOR=#333333]It's rare that my system will boot or takes forever - normally it just hangs / chokes. A reboot from a remote shell used to be pretty quick and I could reconnect within 10 seconds or so. Here's screens shots of where it gets to:[/COLOR]
[COLOR=#333333][URL="http://puu.sh/a38qt/7626e688b8.png"]
Hang Image Compilation[/URL]
[/COLOR]
[COLOR=#333333]I have been told that such may happen after a kernel upgrade if their "hypervisor" doesn't have that kernel and that it may require manual setting from DO's support.[/COLOR]
[COLOR=#333333]I had them mount their ArchLinux recovery disk and checked out the system's /lib/modules: I've been told these are the supported kernels that Ubuntu can run with.[/COLOR]
[COLOR=#333333][URL="http://puu.sh/a37ZQ/7960ee4272.png"]
Directory /lib/modules[/URL]
[/COLOR]
[COLOR=#333333]I set my kernel to: ubuntu 12.04 x64 vmlinux-3.8.0-42-generic From DO's droplet settings.[/COLOR]
[COLOR=#333333]I'm still getting the above hangs and some of the images above were after such.[/COLOR]

---

### Post by slooksterpsv on 2014-07-10
I don't think it's hanging on fsck, it processes fsck and goes to starting the Network and hangs at the network. If you could get the dmesg logs that would help a lot. If you could also disable quiet to where it outputs EVERYTHING while booting, that would help to to find out what's going on.

---

