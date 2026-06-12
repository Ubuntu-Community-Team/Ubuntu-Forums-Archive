---
title: "Wake from suspend video issue with Gutsy"
date: 2007-09-21
forum: General Help
---

### Post by cyli on 2007-09-21
I hope this is the right forum...

I am trying to get suspend to work on my desktop, since I am trying to save a bit on power and I often forget to turn my machine off (or I go away for much longer than expected).  It suspends just fine - only takes a second or two.  When I press the power button, everything seems to start up except that I get no video.  My monitor blinks in that way that means it hasn't gotten any signal.

Hitting ctrl-alt-del does nothing.  I can ping the machine, SSH into it.  When I /etc/init.d/gdm restart, I can get video and everything works as it normally does.  I didn't find anything in /var/log/dmesg or /var/log/Xorg.0.log.  There is some stuff in /var/log/syslog - I've attached a snippet of mine (I also made some line breaks and a comment as to when I ssh-ed in and restarted GDM) but I can't really interpret the information.  The only thing that looked suspicious to me was:

Sep 21 03:51:00 jinchuuriki kernel: [ 1581.544000] sd 2:0:0:0: [sda] Starting disk
Sep 21 03:51:00 jinchuuriki kernel: [ 1582.320000] ata1.01: ACPI cmd f5/00:00:00:00:00:b0 failed (Emask=0x1 Stat=0x51 Err=0x04)
Sep 21 03:51:00 jinchuuriki kernel: [ 1582.320000] ata1.01: revalidation failed (errno=-5)
Sep 21 03:51:00 jinchuuriki kernel: [ 1582.320000] ata1: failed to recover some devices, retrying in 5 secs
Sep 21 03:51:00 jinchuuriki kernel: [ 1585.716000] ata3: port is slow to respond, please be patient (Status 0x80)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1.01: ACPI cmd f5/00:00:00:00:00:b0 failed (Emask=0x1 Stat=0x51 Err=0x04)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1.01: ACPI on devcfg failed the second time, disabling (errno=-5)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1.01: revalidation failed (errno=1)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1: failed to recover some devices, retrying in 5 secs

I've included my /var/log/syslog broken up into snippets:  the messages from after I hit "suspend", messages after I hit the power button to resume, and the messages from after I restarted GDM.

Any suggestions as to what to do or where to look for what may be wrong would help me tremendously.

---

### Post by perbu on 2007-10-13
I've got the same issue. A thinkpad X60 running Gutsy RC1.


Per.

---

### Post by trippinnik on 2007-10-13
Same problem here.  There seems to be a number of bug reports out there about it too [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134476](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134476)

---

### Post by sudo_t43p on 2008-01-22
> **cyli said:**
> I hope this is the right forum...

I am trying to get suspend to work on my desktop, since I am trying to save a bit on power and I often forget to turn my machine off (or I go away for much longer than expected).  It suspends just fine - only takes a second or two.  When I press the power button, everything seems to start up except that I get no video.  My monitor blinks in that way that means it hasn't gotten any signal.

Hitting ctrl-alt-del does nothing.  I can ping the machine, SSH into it.  When I /etc/init.d/gdm restart, I can get video and everything works as it normally does.  I didn't find anything in /var/log/dmesg or /var/log/Xorg.0.log.  There is some stuff in /var/log/syslog - I've attached a snippet of mine (I also made some line breaks and a comment as to when I ssh-ed in and restarted GDM) but I can't really interpret the information.  The only thing that looked suspicious to me was:

Sep 21 03:51:00 jinchuuriki kernel: [ 1581.544000] sd 2:0:0:0: [sda] Starting disk
Sep 21 03:51:00 jinchuuriki kernel: [ 1582.320000] ata1.01: ACPI cmd f5/00:00:00:00:00:b0 failed (Emask=0x1 Stat=0x51 Err=0x04)
Sep 21 03:51:00 jinchuuriki kernel: [ 1582.320000] ata1.01: revalidation failed (errno=-5)
Sep 21 03:51:00 jinchuuriki kernel: [ 1582.320000] ata1: failed to recover some devices, retrying in 5 secs
Sep 21 03:51:00 jinchuuriki kernel: [ 1585.716000] ata3: port is slow to respond, please be patient (Status 0x80)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1.01: ACPI cmd f5/00:00:00:00:00:b0 failed (Emask=0x1 Stat=0x51 Err=0x04)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1.01: ACPI on devcfg failed the second time, disabling (errno=-5)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1.01: revalidation failed (errno=1)
Sep 21 03:51:00 jinchuuriki kernel: [ 1587.700000] ata1: failed to recover some devices, retrying in 5 secs

I've included my /var/log/syslog broken up into snippets:  the messages from after I hit "suspend", messages after I hit the power button to resume, and the messages from after I restarted GDM.

Any suggestions as to what to do or where to look for what may be wrong would help me tremendously.

I think there is no idea looking for an answer in log files because in that state write access to hdd is not available (or am I wrong?).

---

### Post by pointone on 2008-01-22
I had a similar problem which I solved by editing /etc/default/acpi-support and changing the following:

```
SAVE_VBE_STATE=false
POST_VIDEO=false
```

---

