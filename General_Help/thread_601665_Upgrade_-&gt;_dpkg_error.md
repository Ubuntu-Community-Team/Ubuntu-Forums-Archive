---
title: "Upgrade -&gt; dpkg error"
date: 2007-11-03
forum: General Help
---

### Post by Guises on 2007-11-03
This is sorta double-posting, but I figure separate posts for separate problems. Original thread is here:

[http://ubuntuforums.org/showthread.php?p=3697199#post3697199](http://ubuntuforums.org/showthread.php?p=3697199#post3697199)

The short is that my dependencies appear to be screwed up - running the update manager or anything dealing with a package installer spits out:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
But running "sudo dpkg --configure -a" gives:
> Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
dpkg: dependency problems prevent configuration of util-linux-locales:
util-linux-locales depends on util-linux (>= 2.13-0); however:
Package util-linux is not installed.
util-linux-locales depends on util-linux (<< 2.13.0-0); however:
Package util-linux is not installed.
dpkg: error processing util-linux-locales (--configure):
dependency problems - leaving unconfigured
Setting up libc6 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
I got the impression from that that I needed the util-linux package but "sudo aptitude install util-linux" gives me the same error that apt-get and synaptic do. Downloading the deb file and trying to install via the GDebi installer gives me an error that explicitly says that my dependencies are screwed up.

Anyway, I'm at something of a loss now. Searching other threads for dpkg 135 errors suggests that it might be java that's screwed up, but I don't know how to reinstall that if the package managers aren't working.

---

### Post by Guises on 2007-11-04
Well, alright. Guy in the other thread is helping me there, so just ignore this one (sorry).

---

