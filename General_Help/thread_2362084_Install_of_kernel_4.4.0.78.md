---
title: "Install of kernel 4.4.0.78"
date: 2017-05-23
forum: General Help
---

### Post by sz.czubek.8t0 on 2017-05-23
Hi to Everyone,

recently I got a number of error messages during last week's installation (successful, I guess) of kernel 4.4.0-78 (currently I have three kernels present on the computer: 3.19.0-80, 4.4.0-77 and 4.4.0-78), and since I'm an inexperienced Ubuntu user, I was wondering if this is something to be worried about.

the error messages were, for example:
- Warning: Stopping snapd.service, but it can still be activated by:
  snapd.socket

- N: Ignoring file "50unattended-upgrades.ucf-dist" in folder "/etc/apt/apt.conf.d/", because it has a wrong file extension 
(this one was repeated a few times)

- : Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.

- Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
(this one was repeated several times)

1. Was wondering, if the old kernel is the issue here, and if so, then is removing it necessary for the system to run properly in the future (now, everything seems to be fine on the surface, but maybe with subsequent updates and installations it will cause more and more "internal conflicts" and later on build into a bigger problem ?)

2. I've noticed that some of the above messages also appeared during updates of the other components of the system.

3. Also, is it possible that removing this older kernel will cause some features of the system to cease working properly ? (for example the sound).

I mentioned sound, because this feature is very important for me, and getting it to work properly (headphones / ext. speakers), while not aware to tread carefully, was unfortunately the reason for a very turbulent first week or two of my experience with ubuntu (starting this may).
Short story short, I did some reckless stuff with updating the system, removing software, reinstalling it again, even trying (unsuccessfully) installing another linux distros, because of which I finally ended with a damaged grub (now repaired) and had twice or even thrice to restore the laptop to factory settings (14.04 LTS).
But currently (16.04.2 LTS) everything seems to be fine, even though I still don't exactly know what finally "stabilized" the sound: the successful upgrade to 16.04.2, or the tips I followed from other threads in this forum, eg. added line in "alsa.b.config" and enabling "auto-mute" in alsamixer) - except for those errors in the log.

Looking forward to some advice concerning those error messages (if anyone could cast an eye sometime, thanks).

---

### Post by howefield on 2017-05-24
Post moved to its own thread and to the "*General Help*" forum for a better fit.

---

