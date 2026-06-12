---
title: "Help! VMware inexplicably won't start!"
date: 2007-04-22
forum: General Help
---

### Post by Blueshell on 2007-04-22
In Dapper, I just discovered that clicking on the VMware Server Console causes the cursor to spin for a few seconds, and then it just bombs out, leaving me with no console---as if I didn't click on it in the first place.  I've checked in /var/logs and in /etc/vmware and can't see -any- log entries related to this at all, so I can't even figure out what's failing.

Where should I look next?

I infrequently run VMware---the last time was probably 2-3 months ago---so I'm worried that some Dapper update bashed VMware somehow, but what?  Without any error messages I'm helpless.  I'm currently running kernel 2.5.15-28, but I also tried -27 and -23 (previous kernel versions on this machine), and the behavior is identical.

Help?

---

### Post by Mike'sHardLinux on 2007-04-22
Try running vmware from the commandline. That might give you an error.

If nothing else, just re-install it. IIRC, when you get a kernel update, you have to re-install vmware for the new kernel.

If you do re-install, you might want to make sure you have the latest vmware, just in case there's some bug fixes or other important updates.

---

### Post by hikaricore on 2007-04-22
Yea you probablly just need to recompile the module for vmware.

Running it from a terminal window will tell you how to do this.

---

### Post by Blueshell on 2007-04-22
Yup!  And of -course- it occurred to me to run it from the command-line about 30 seconds before the first response to this post...   If run from there, it says you need to run /usr/bin/vmware-config.pl, which (unfortunately) asks a bunch of questions (making it hard to script) but does in fact rebuild everything, and my VMware works again.

And I realized why even my -27 kernel, which was what I'd -built- VMware for, was no longer working---if I recall correctly, Ubuntu slipped in a kernel update a few months ago that -didn't change- the -27 version, even though it was a new kernel!  I recall seeing something like this go by while installing, but the backups I had of old kernels were wiped out when I had to rebuild my backup server just a month ago (go figure), so I can't rigorously check if this was the problem.  But my -27 kernel image in /boot is definitely -newer than- the logfile showing when I built VMware, which is -impossible- given that I was building for -27, unless that -27 kernel was replaced by a newer (sub)version with the same so-called name, aka -27, sometime after I built VMware.  Geez, I wish Ubuntu hadn't done that...

Of course, I had to download the -28 kernel headers too (I assume) to rebuild.  It's kinda poor that the icon-based version simply quits w/o no errors and no logging; at least now I know that the command-line version is more helpful.

(It'd be really handy if there was a VMware package that dealt with downloading the latest version, making sure your kernel headers were installed, and then rerunning vmware-config.pl whenever a new kernel was grabbed by Synaptic.  Know of any such thing?  Bonus if it would then uninstall the older kernel-headers packages; I need to go back and do that for -27 now...)

Anyway, VMware works again.  Now I should install -again- to pick up 1.0.2, since I'm currently running 1.0.1.

Thanks!

---

