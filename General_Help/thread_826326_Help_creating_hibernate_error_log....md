---
title: "Help creating hibernate error log...?"
date: 2008-06-11
forum: General Help
---

### Post by ethanay on 2008-06-11
Hello,

I have a strange hibernate error:

1) I invoke hibernate, screen goes black
2) there is a brief pause, then drm_sysfs_suspend appears and starts
...and at the very end of the process, right before power off
3) a failure message flashes RIGHT after the hard disk turns off, causing it to suddenly power up again to print/write the failure message
(like a hiccup)
4) the system shuts down
5) power on
6) the boot process finds the restore image successfully and loads it back into memory
7) I am fully resumed, with the error message about a failure
8) I cannot find the error message in ANY log file in /var/log
-------------------
It is usb-related, and I think it may be this bug:
[https://bugs.launchpad.net/ubuntu/+bug/229932](https://bugs.launchpad.net/ubuntu/+bug/229932)

However, I can't for the life of me find the error message, which leads me to believe it isn't logged.  It appears too briefly for me to remember/write anything down except bits and pieces.  How can I ensure that the error is saved to a log?

anyway, I haven't been able to find clear directions on creating a hibernate log file, so hopefully someone can help clear this up...

thanks,
ethanay

---

### Post by iaculallad on 2008-06-11
Try looking at the **/var/log/kern.log** file.

---

### Post by ethanay on 2008-06-12
Hello,

thanks for the suggestion -- i've tried that and the error isn't present.  It should be the last thing logged before entering hibernation -- if it was logged at all.  The hard drive starts up again for a split second just after shutting down in order to print the message, but I can't find it saved anywhere...it seems like a tricky situation.  I think maybe it's not getting logged...?

---

