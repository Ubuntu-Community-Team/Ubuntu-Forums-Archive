---
title: "rtcwake help"
date: 2014-01-10
forum: General Help
---

### Post by joe52 on 2014-01-10
Need help, had 12.04 server on a pc for 2 years as a file server, etc.  One thing i did was have rtcwake as a cronjob to shut off every night and turn on in the morning.  I had to rebuild the pc, and used another one i have since it has more ram, and is 64 bit, so i did a fresh install of 12.04.  I have my PC bios set to S3 power mgmt.  I used this command on my old box, sudo /usr/sbin/rtcwake -m mem -s 15 and it never comes back on with my test in 15 sec, unless i hit the pwr button.  Looked at the man page and tried this, sudo /usr/sbin/rtcwake -m disk -s 15, and it turned off, and turned back on.  Tried it again, and this time, it was stuck on the grub boot menu.  I gave it a few mins, and no luck.  Finally pressing enter brought the pc back from sleep to a prompt.

Problem is that i keep this pc in a closet w/o a keyboard and monitor, just plugged into the network, backup ext HD and power, and dont want to hook up a keyboard everytime to hit enter every morning.  I have searched google for this and just keep coming up with the man pages for rtcwake.

I like using rtcwake since it allows me to put the pc in standby overnight when i'm not using it and come on in the morning.  It worked fine on my other pc for a few years.  I am runnning the 3.8.0-35-generic kernel, and on my old one before i rebuilt it had .57 on it.  I was wondering if the kernel has anything to do with it.  Just dont know why after it wakes the first time it boots fine, but the 2nd time it hangs on the grub boot menu.  I have it set to 0, to start automatically on the default on my list.

I was wondering if anybody else has ran into this issue, or what else i can check.  I have tried searching online, but no good results.

Thanks.

---

