---
title: "Finding the root cause of a system freeze"
date: 2020-02-05
forum: General Help
---

### Post by d2105284 on 2020-02-05
I'm using Bionic and this machine sometimes causes the system to somehow freeze.  I'll be doing something and all of the sudden both monitors go to sleep as if the system was suspended.  However based on the system's power indicator it is not in suspend mode.  No keyboard or mouse events will "resume" the system nor will touching the power (which is already set to *do nothing *when pressed).  It seems as though the only option is to pull the power cable and reboot.
The last time this happened when I had rebooted I ran a [FONT=courier new]tail -f /var/log/dmesg > ~/log[/FONT] but upon booting back in there was nothing in there that wasn't there when I booted.

Since this lockup always happens when I'm right in the middle of something it's getting very frustrating and I'm looking for any tips that will help me narrow it down.

---

### Post by deadflowr on 2020-02-05
You can use journalctl command to see information about the last boot session(or any previous boots)
```
journalctl -b -1 | tail
```
will output the last thing done on last boot session before the system was shutdown.

(-1 means the previous session before the current (running) session.
You can use -2 or -3 or beyond that if need to be to see any previous sessions)

---

### Post by TheFu on 2020-02-05
First, prove that the system is really locked up, not just a GUI thing.
[https://ubuntuforums.org/showthread.php?t=2435749](https://ubuntuforums.org/showthread.php?t=2435749)

I don't have 18.04, but there are **journalctl** settings that will keep xMB of logs or the last y-boot logs. My systems didn't retain boot logs beyond the current boot. Those were/are the default settings.

/etc/systemd/journald.conf has the settings. There is a manpage for that file which explain the options.
```
Storage=persistent
```
I had to create a directory in /var/ somewhere too.  That's covered in the manpage too.  Be certain to use the manpages ON-THE-SYSTEM since everything related to systemd is in active development.  I've read that manpages for systemd stuff is "aspirational", not necessarily how it really works today.  That was years ago, so perhaps they corrected that problem to have correct manpages for the correct version?

---

### Post by d2105284 on 2020-02-13
OK I need to reopen this.

```
$ grep Storage /etc/systemd/journald.conf
Storage=persistent
$ journalctl -b 1 | tail -n1
Jan 21 13:42:34 F5KNM0NZF9VM systemd-journald[11964]: Journal stopped
```

System has crashed three times today; I've booted four times today so I should see Feb 13 not Jan 21.

---

### Post by TheFu on 2020-02-13
Did you happen to create the required directory and tweak the journal size as spelled out in the manpage  too?

---

### Post by daniewicz on 2020-02-13
Memory problem? Run memtest to ensure there are no RAM problems.

---

### Post by deadflowr on 2020-02-13
```
journalctl -b 1 | tail -n1
``` 
isn't what i posted to run.
Run what I posted.
There is a big difference between 1 and -1.
And just use tail by itself, no need to set a defined line number. 
The default 10 lines should be fine.

---

### Post by d2105284 on 2020-02-14
> **TheFu said:**
> Did you happen to create the required directory and tweak the journal size as spelled out in the manpage too?I did not create the directory, because of what the manpage says:


*If "persistent", data will be stored preferably on disk, i.e. below the /var/log/journal hierarchy (which is **created if needed**), with a fallback to /run/log/journal (which is created if needed), during early boot and if the disk is not writable.*


> **deadflowr said:**
> ```
journalctl -b 1 | tail -n1
``` 
isn't what i posted to run.
Run what I posted.
There is a big difference between 1 and -1.
And just use tail by itself, no need to set a defined line number. 
The default 10 lines should be fine.Yes, you are right, I missed a character when I typed it in. Big difference. And -n1 isn't line number, it's number of lines. I didn't think it was necessary to output 10 lines when the last line was enough to demonstrate my confusion of the logs being "old"


Running it correctly with - shows this:```
Feb 13 15:17:36 hostname slack.desktop[2816]: [02/13/20, 15:17:36:359] info: [API-Q] (ABC) def-1234.355 conversations.mark called with reason: viewed
Feb 13 15:17:36 hostname slack.desktop[2816]: [02/13/20, 15:17:36:360] info: [API-Q] (ABC) def-1234.355 conversations.mark is ENQUEUED
Feb 13 15:17:36 hostname slack.desktop[2816]: [02/13/20, 15:17:36:360] info: [API-Q] (ABC) def-1234.355 conversations.mark is ACTIVE
Feb 13 15:17:36 hostname slack.desktop[2816]: [02/13/20, 15:17:36:669] info: [API-Q] (ABC) def-1234.355 conversations.mark is RESOLVED
Feb 13 15:17:38 hostname slack.desktop[2816]: [02/13/20, 15:17:38:562] info: [FOCUS-EVENT] Client window blurred
Feb 13 15:17:38 hostname slack.desktop[2816]: [02/13/20, 15:17:38:570] info: [DESKTOP-SIDE-EFFECT] Update from desktop for keys  ["windows"]
Feb 13 15:17:38 hostname slack.desktop[2816]: [02/13/20, 15:17:38:620] info: [DESKTOP-SIDE-EFFECT] Update from desktop for keys  ["windows"]
Feb 13 15:18:01 hostname CRON[5198]: pam_unix(cron:session): session opened for user me by (uid=0)
Feb 13 15:18:01 hostname CRON[5199]: (me) CMD (rm -f ~/somedir/*)
Feb 13 15:18:01 hostname CRON[5198]: pam_unix(cron:session): session closed for user me
```
Slack is pretty noisy in its logging and several similar lines exist further up.  I don't know the exact time the monitors turned off, but there's certainly nothing abhorent in those lines

---

