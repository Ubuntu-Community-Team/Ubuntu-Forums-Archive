---
title: "Acer Aspire 5670 - Boot interuption / Pause"
date: 2007-04-26
forum: General Help
---

### Post by lw5 on 2007-04-26
I just installed Feisty on an Acer Aspire which seems to work fine, except for one thing:

During boot, somewhere halfway, the process gets stalled for half a minute or so. At first I thought ubuntu was mounting my fat partitions, but outcommenting their lines in /etc/fstab didn't help.

I found one previous mentioning of the problem [_here_](http://gez.plain.at/blog/ubuntu/installing-ubuntu704-feisty-fawn-herd2-on-an-acer-5672wlmi-laptop/) (between the dmesg part en the ati driver part).

Are more people experiencing this problem? What is its cause and is there a way around this?

---

### Post by lw5 on 2007-04-27
* kick, nobody?

As far as I can find now, it could be something with fsck or with the network interfaces settings (can't try yet, don't have the laptop here) [[_link_](http://ubuntuforums.org/showthread.php?t=423282&highlight=fsck)

---

### Post by lw5 on 2007-04-29
Last kick :| 

Not even someone having this on a different laptop or desktop pc?


Edit: It seems to be a bug in which fsck is checking FAT partitions on bootup: [_launchpad bugreport_](https://bugs.launchpad.net/ubuntu/+source/dosfstools/+bug/59293)

---

