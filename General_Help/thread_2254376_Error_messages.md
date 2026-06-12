---
title: "Error messages"
date: 2014-11-26
forum: General Help
---

### Post by heroquestelf on 2014-11-26
Where do I find the log files for error messages?

My laptop is running 13.04. Basically right before it pulls up the login screen it flashes a series of error messages, and it goes by so quickly that I can't write it down. Is there a file somewhere on my machine where I can pull those error messages back up again so I can diagnose my system and see what the problem is?

If it helps at all, I **think** I know what the problem is. I recently installed a new DVD-Rom and that's when the error messages started.

---

### Post by deadflowr on 2014-11-26
Most system log files are found in /var/log.
Any crash report would be in /var/crash.

It's unclear what those errors would be, but probably look in the log files for xorg, dmesg, kern,and syslog.
Just for starters.

Also, 13.04 has reached end of life and is no longer supported by the Ubuntu developers and the Ubuntu Community.
You might look at either upgrading to a supported release, or installing a supported release.
Supported releases right now are 12.04, 14.04, and 14.10.

We will keep this open if you need help figuring out what to do about that.

---

### Post by heroquestelf on 2014-11-26
okay... I'll look into changing, but I'll go into that in a second. I was able to write down some of the error messages. It was a "Buffer I/O error on device" error. Is there a way to search the log files all at once for that error?


SECONDLY: I'd LOVE to upgrade to 14, (in fact, I did... twice) but I'm having a graphics card issue. I have my laptop attached to my Panasonic TV. When I run video files on my laptop by itself, they run fine, but when I attach the external monitor, it drags like I'm trying to run two WoW clients as the same time, and the refresh rate goes to CRAP.

Any ideas on how to fix this?

---

