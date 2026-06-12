---
title: "System Problem Detected when its been working fine for months"
date: 2013-04-07
forum: General Help
---

### Post by BmanTheBoss on 2013-04-07
I have one of my laptops running Ubuntu Desktop 12.10. Its been working fine for the months I've had it running on Ubuntu. Only thing is, every 3 minutes or so it says "System Problem Detected. Would you like to report the problem?" So I did once, and I know the effects wouldn't be immediate, but nothings happened. I read the little error report it gave me, but it didn't help. Can someone help me get this annoying thing away?

---

### Post by r-senior on 2013-04-07
Do you know which program is causing the crash? What did you report the problem against?

---

### Post by BmanTheBoss on 2013-04-07
It says "Ubuntu 12.10 has experience an internal error", so I don't think it's a program as much as the system.

---

### Post by rnerwein on 2013-04-07
hi
in the pop-up window must be a button called "details". klick on it and have a look where the problem comes from.
ciao

---

### Post by r-senior on 2013-04-07
Sometimes those error messages mask what the real problem is. Is it still happening, can you get more details from Apport when it shows the crash dialog?

Do you have anything in /var/crash? Is there anything in /var/log/apport.log or /var/log/syslog?

---

### Post by schragge on 2013-04-07
There's a [post=12587800]known problem[/post] with the script */usr/share/apport/apport-gpu-error-intel.py*. Perhaps you are affected by it?

---

### Post by BmanTheBoss on 2013-04-07
In /var/crash, there are 4 .crash files, one .upload file, and one .uploaded file and in /var/log/apport.log there is nothing, and in /var/log/syslog theres a lot of code. I think it may have something to do with the system resuming or somewhere along that line because when I suspend it and open it back up, this happens the most.

---

### Post by BmanTheBoss on 2013-04-07
I'm also thinking, what if I reinstalled the OS? Might that fix it?

---

### Post by VirginiaDrifter on 2013-04-07
I'm having the same problem.

In var/crash I have 5  /var/crash/xserver-xorg-video-intel.2013-04-04_14:19:28.011108.crash
and 10 /var/crash/xserver-xorg-video-intel.2013-04-04_14:19:39.770423.uploaded
  
2   /var/crash/_usr_bin_update-manager.1000.upload
and 1  /var/crash/_usr_bin_update-manager.1000.crash

apport.log is empty

syslog looks normal, just shows where it ran cron jobs and not showing any errors

---

