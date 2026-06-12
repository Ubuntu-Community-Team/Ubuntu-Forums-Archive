---
title: "Latest Kernels Not Booting"
date: 2013-02-21
forum: General Help
---

### Post by Katla on 2013-02-21
Installed available updates today, including a new package of headers and kernels. Saw that my boot partition was full, so went to clear out some of the old ones. I've been doing that manually and thinking how much that sucked when I came across Ubuntu Tweak. Didn't even know I already had it installed. It was exactly what I'd been wanting in Ubuntu. So I ran the Janitor, cleaned out all the old crap on the machine, then went ahead with the installation of the new kernel. Restarted and found I had a problem. Wouldn't reboot using the new kernel, normally or in safe mode. So I booted with the kernel I'd just replaced. No problems. 

I have no idea what the issue could be. It's not pressing, as I have no issue with the kernel I am using presently, and rarely reboot my machine as it is. But I am concerned if this will be an issue going forward. I can easily wait for the next new kernel to come along, and see if that works, but, again, I don't want to sweep anything under the rug if there's a chance I'll just be compounding my problems. 

Is there a way for me to test the kernel or get some sort of diagnostic on it? Is it possible that when I used Tweak I got rid of a component that wasn't vital to the older kernel but was necessary for the newer? 

Thank you for any advice you may have.

---

### Post by dino99 on 2013-02-21
all the systems around on earth are not really of install & forget  ;)
doing some maintenance is not loosing your own time; dont hesitate to use:

-clean/autoclean/autoremove
-gtkorphan, bleachbit

if you have an issue with only one kernel, then purge it (using synaptic for example), check that "dkms" is installed, then reinstall it.

But remember that logs are your best friends to find usefull warnings/errors to fix/report issues (watch .xsession-errors & /var/log/dmesg, & ...)

---

