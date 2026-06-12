---
title: "[CLOSED] stuck at emergency mode prompt"
date: 2017-07-23
forum: General Help
---

### Post by bric on 2017-07-23
I have a pc running Ubuntu 17.04.  Things have been fine since ...well, 16.04 and through the upgrade in April/May this year.  Yesterday, I shutdown and when I restarted I greeted with:

```

[   1.968415] radeon 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
/dev/sdc6: recovering journal
/dev/sdc6: clean, 673436/2588672 files, 4152063/10338560 blocks
You are in emergency mode.  After logging in, type "journal -xb" to view system logs, "systemctl reboot" to reboot, "systemctl default" or "^d" to try again to boot into default mode.
Give root password for maintenance
(or press Control-D to contniue):

```

pressing ^D just returns me to the same prompt.

The logs weren't particularly helpful to me.  There were a couple things in red.  One of which was the above PCI ROM... message.  I would look now but I'm typing this via a live USB and it's late enough that I won't have the energy until tomorrow. Is there a way to pull the logs from the live USB? Or a good way to save the log? Or is that even useful?

Any help on how to solve this is appreciated.

---

### Post by #&amp;thj^% on 2017-07-23
Sorry to hear this and it has been showing up as the links below.  (Also are you fully updated?)

[https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/879418-why-the-r9-290-other-select-radeon-gpus-are-performing-miserably-on-linux-4-7/page2](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/879418-why-the-r9-290-other-select-radeon-gpus-are-performing-miserably-on-linux-4-7/page2)

[https://ubuntuforums.org/showthread.php?t=2355798](https://ubuntuforums.org/showthread.php?t=2355798)

[https://bugs.freedesktop.org/show_bug.cgi?id=98798](https://bugs.freedesktop.org/show_bug.cgi?id=98798)

I would be curious if booting to a older kernel might help?

---

### Post by bric on 2017-07-23
I was fairly updated (though haven't updated in the last week that I recall).  4.10.00-28 is the default newest kernel  I tried booting from 4.10.00-21 (oldest) and same thing.

Also, I pulled the video card and it does the same thing with that removed.
I think I will use this as an opportunity to play with a different distro.  All my data is on a different drive so aside from program installation/configuration headaches it should be a fairly easy move.

Thanks for the help.

---

