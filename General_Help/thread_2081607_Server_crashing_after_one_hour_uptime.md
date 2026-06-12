---
title: "Server crashing after one hour uptime"
date: 2012-11-07
forum: General Help
---

### Post by MikkyX on 2012-11-07
Hi,
We've got an Ubuntu 11.10 server which we use for LAMP web development here in the office. A couple of times in the past, it's gone through a phase where it reboots after it's been up for one hour. It's not a specific minute within an hour - it's just after one hour of uptime. 

The last time this happened it seemed to fix itself after an apt-get update / upgrade on the installed packages. I've done this again just now and it doesn't seem to be helping. Still reboots. I can't use acpi to get any temperature readings as the machine either doesn't have sensors, or those it does have aren't visible to the install.

Ordinarily I could take a little extra time to fix this (we're primarily a Windows developer and the Linux box is kind of my baby) but I'm working on a MASSIVE PHP project right now and need this fixed in a hurry so a dist upgrade isn't really an option right now.

Anyone got any thoughts on things I could try, or look at? All help appreciated.

---

### Post by rubylaser on 2012-11-07
Have you looked at the log files?  That's the best way to figure out the issue.

```
/var/log/kern.log
/var/log/syslog
/var/log/messages
```

Any application specific logs (Here's Apache for an example)
```
/var/log/apache2/error.log
```

---

### Post by MikkyX on 2012-11-07
I'll check those, thanks. :)

---

### Post by MikkyX on 2012-11-07
OK, the first two don't contain anything that gives the cause away (or at least, not in a way I can make much sense of!) and I apparently don't have a /var/log/messages file. Will keep looking...

---

### Post by MikkyX on 2012-11-07
I've cleared some old kernal images from /boot (I was getting an error telling me it was a bit full) but it's just rebooted again - I can't make sense of anything in the logs.

I went to the server and watched to see what happened - right on time, it just clicked off and reboot. No errors on the screen, no messages flashing up right before the off - it just went dark, and was back up again a couple of minutes later.

---

### Post by 2F4U on 2012-11-07
/var/log/messages has been deprecated since 11.04. You can find the same info in /var/log/syslog.

---

### Post by MikkyX on 2012-11-07
> **2F4U said:**
> /var/log/messages has been deprecated since 11.04. You can find the same info in /var/log/syslog.

Ah - found that! Next time the server falls over (should be, oooo, about 15 minutes from now) i'll check that file and post the last few lines before reboot. See if there's anything useful in there.

---

