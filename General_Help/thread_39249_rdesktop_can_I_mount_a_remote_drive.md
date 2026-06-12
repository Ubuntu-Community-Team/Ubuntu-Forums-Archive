---
title: "rdesktop: can I mount a remote drive?"
date: 2005-06-04
forum: General Help
---

### Post by shakin on 2005-06-04
I'm currently setting up some software on a remote Windows box and I only have remote desktop connectivity through the firewall. Is there a way to mount the remote drives so I can transfer files? Any way at all to transfer files?

Thanks.

---

### Post by Darrena on 2005-06-04
You can with rdesktop version 1.4 or later, the TSClient and and the rdesktop version that come with Hoary do not support mapping drives.

There are Debian packages available for rdesktop 1.4.1 here:
[http://packages.debian.org/unstable/x11/rdesktop](http://packages.debian.org/unstable/x11/rdesktop)

The package worked for me except that it failed to install the rdesktop executable properly so I had to run it from usr/bin directly.

To map a drive use a command like this:
usr/bin/rdesktop -r disk:USB=/media/usbdisk 10.10.10.10

At this time the grdesktop front-end does not support redirection so it must be done via a command line.

---

### Post by shakin on 2005-06-04
Awesome, thanks :)

---

