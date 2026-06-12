---
title: "System mysteriously hangs soon after boot even while idle"
date: 2007-06-02
forum: General Help
---

### Post by tarkus on 2007-06-02
I had a frankenfeisty install on my machine which I recently opted to replace with a brand-spanking-new install.  I grabbed the alternate cd (I use lvm over md) and installed.  After waiting half an hour for lvm to come up on the install cd (!) I made my new LV and installed and whatnot.  I boot off the new filesystems and... whammo, hang.  Reboot and try again - hangs again (this time in the middle of replaying the ext3 journal, which scares me greatly)

The gist is, I can boot up fine.  I usually get to the login screen (unless fsck has to run, in which case it hangs there).  I even logged in, ran apt-get update, and then "sudo rmmod lp" (I wanted to try to get the kernel to print something, I'm running netconsole and wanted to make sure it works)

Then it hangs.  The cursor is still blinking on the next prompt.  No disk activity, no kernel panic, netconsole is silent.  Same symptoms every time.  I'm not sure how to troubleshoot this - there's no apparent pattern to when it hangs except that it's an arbitrary (very short) amount of time after boot.  Any help?

For the record, a custom 2.6.16.41 kernel (on a different root fs though) works fine.

Thanks,
Steven

---

### Post by tarkus on 2007-06-02
Aha - a bit more information.  It does not hang in singleuser mode (at best as I can tell), only after completing the startup sequence.
Trying to rmmod netconsole causes the process to hang (rendering the system unusable as it's the only open shell), but leaves the console responsive to keypresses and the magic SysRq key.  (If I let it go all the way, sysrq doesn't do anything)


Another update - the same kernel crashes on the old root fs.  So it seems to be a problem with the kernel or drivers or something.

---

### Post by tarkus on 2007-06-04
I compiled stock 2.6.21.3 sources with make-kpkg and everything works fine.  Should this be filed as a bug, or does anyone have anything to say?  At all?

---

