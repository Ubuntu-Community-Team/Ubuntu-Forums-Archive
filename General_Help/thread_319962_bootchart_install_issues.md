---
title: "bootchart install issues"
date: 2006-12-16
forum: General Help
---

### Post by PhilOSparta on 2006-12-16
I just downloaded bootchart after looking at a number of threads that discuss how handy this program is to diagnose boot speed issues. ( Used synaptic to download and install to my new edgy install )

Some indicate that it works "right out of the box".  Others indicate that they don't get the log generated at /var/log/bootchart and request help.
I'm on of the latter.  The install by synaptic created the /var/log/bootchart directory but there is no log generated after rebooting.

I have spent several hours looking for documentation on how to get bootchart installed to no avail.  ( other than use synaptic and run it )

I've tried to place bootchart into the grub  /boot/grub/menu.lst file.  That was recommended by several other distros.  That didn't work.  

Any ideas?

Phil

---

### Post by DarkN00b on 2006-12-16
I am obviously not familiar with your specific situation, but bootchart will not run or produce a chart if fsck checks the disk at boot time. Could this be your problem?

---

### Post by PhilOSparta on 2006-12-16
> bootchart will not run or produce a chart if fsck checks the disk at boot time. Could this be your problem?  Thanks for the tip.   Unless fsck "always" runs at boot time, which I am not aware of, then that could be the problem.  The typical boot doesn't look like it's checking any particular file systems at boot time.  I've booted about 50 times this afternoon several of which tested the file systems.  Still no bootchart files were generated.

---

### Post by DarkN00b on 2006-12-16
Tha't odd, I've never seen that activity before. FSCK runs at every boot, it just doesn't check *every* time. Maybe someone with more Linux experience can help you.

---

### Post by Draku on 2007-01-26
I get this error on install and on unnistall :|

Setting up bootchart (0.9-0ubuntu6) .
perl: warning: Falling back to the standard locale ("C").
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
/usr/sbin/mkinitramfs: line 13: getopt: command not found
Terminating...
dpkg: error processing bootchart (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bootchart

---

### Post by sc00ter on 2007-03-11
Hi, I have exactly the same issue on my Edgy box. "sudo apt-get install bootchart", I see the "/var/log/bootchart" directory but remains empty no matter how many re-boots I perform.

Anyone know how to resolve this? I've googled, until I can google no more. Help !?! :confused:

---

### Post by SnakeSkin on 2007-10-07
I realized today that the reason that I was not getting a graph was due to a line in my /boot/grub/menu.lst file.

I added profile at the end. It stopped bootchart from working. Removing the option and I have graphs again.... Odd.

---

