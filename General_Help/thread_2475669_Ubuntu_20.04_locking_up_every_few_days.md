---
title: "Ubuntu 20.04 locking up every few days"
date: 2022-06-03
forum: General Help
---

### Post by bmdavis2 on 2022-06-03
I do not believe that I am particularly heavy in resource usage. This last time, I had a few browser tabs open and RStudio. It occurred around 21:10. The screen goes black and the power light on the CPU is on. I must hard boot to get it back up. I checked the syslog and there is nothing obvious that is causing a problem, but I also may not recognize a problem if it is there.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290565&stc=1[/IMG]

---

### Post by TheFu on 2022-06-04
Use **journalclt -b -1** to see the last set of hardware issues from the prior boot.

Please don't post images for text. 
Actually, that image isn't useful. We need to see warnings and errors, not a reboot.

---

### Post by bmdavis2 on 2022-06-04
I ran journalctl -b -1 (not journalclt) and at that time frame, the message is the same. Is there some other log that will provide more useful information?

---

### Post by TheFu on 2022-06-04
Lots of logs.  They are in /var/log/ somewhere.
But if you rebooted the system, the -1 option needs to be the number of reboots prior to the current one where the error was seen.
You can also ask for errors. There's an option for the journalctl program to have those output.  The manpage explains all of this.

---

### Post by dragonfly41 on 2022-06-04
glogg is one useful log file viewer which looks through log files for keywords such as WARNING, ERRORS .. (you create the search patterns). Sorts the wheat from the chaff. Thee are others which search log files. Even ripgrep will do that.

---

