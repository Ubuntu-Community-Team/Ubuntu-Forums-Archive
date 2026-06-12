---
title: "System Freeze Question"
date: 2008-06-02
forum: General Help
---

### Post by jbaerbock on 2008-06-02
Ok so I was playing WoW (never had a problem before). Suddenly tonight the system freezes completely, not shortcuts or commands work. I looked in my syslog and the following looks off to me:

Jun  2 01:36:48 ChiiBit syslogd 1.5.0#1ubuntu1: restart.
Jun  2 01:36:48 ChiiBit anacron[5391]: Job `cron.daily' terminated
Jun  2 01:36:48 ChiiBit anacron[5391]: Normal exit (1 job run)
Jun  2 01:37:09 ChiiBit kernel: [  296.856803] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Jun  2 01:37:10 ChiiBit kernel: [  297.676258] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Jun  2 01:49:58 ChiiBit -- MARK --
Jun  2 02:09:58 ChiiBit -- MARK --
Jun  2 02:17:01 ChiiBit /USR/SBIN/CRON[6713]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  2 02:29:58 ChiiBit -- MARK --
Jun  2 02:49:58 ChiiBit -- MARK --
Jun  2 02:59:12 ChiiBit kernel: [10328.475483] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Jun  2 02:59:13 ChiiBit kernel: [10329.157910] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Jun  2 03:09:58 ChiiBit -- MARK --
Jun  2 03:17:01 ChiiBit /USR/SBIN/CRON[6897]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  2 03:29:59 ChiiBit -- MARK --
Jun  2 03:33:31 ChiiBit syslogd 1.5.0#1ubuntu1: restart.

The last entry for restart took place when I had to hard reboot the system and the first entry was when I restarted normally earlier that evening. Keep seeing the CDROM not ready line. Any idea from this code what went wrong?

---

### Post by sdennie on 2008-06-02
Nothing looks particularly suspicious to me.  It probably won't help but, you can more or less render your CDROM idle by doing:

```

sudo hal-disable-polling --device /dev/scd0

```

Running an nvidia card, I've sometimes had odd hangs (or crashes) and, sometimes they are easy to fix by hitting Ctrl-Alt-F1 and then hitting Ctrl-Alt-F7.

---

### Post by jbaerbock on 2008-06-02
What do those two combinations do exactly? I have an ATI card which finally works with WoW, is it maybe because I tried running WoW in fullscreen instead of windowed like I had been doing before with no errors? 

Everytime I have a freeze up in fullscreen there seems nothing I can do (tried ctrl+alt+del , ctrl+alt+backspace, and a few others) but nothing ever seems to correct it so im forced to hard reboot sadly.

---

### Post by sdennie on 2008-06-02
Ctrl-Alt-F1 then Ctrl-Alt-F7 will take you out and then back into X windows.  It has sometimes fixed problems for me with nvidia cards.

---

### Post by jbaerbock on 2008-06-04
I'll note them down. For now windowed mode seems to work best anyway so I'll stick to it.

---

