---
title: "Clone Ubuntu install from HDD to SSD...question about configuration."
date: 2019-12-23
forum: General Help
---

### Post by RallyDarkstrike on 2019-12-23
Quick question - when _***CLONING***_ from an  HDD to an SSD, will Ubuntu detect it is now on an SSD and then enable SSD specific settings like TRIM, etc automatically (Windows 10 configures all this automatically when installed OR cloned to an SSD), or would I  have to do it myself...?

I know from a FRESH INSTALL to an SSD Ubuntu will adjust everything correctly, but if it is _***cloned ***_to an SSD, will it do so as well?

The install in question is already running the EXT4 file system.

Thanks!

---

### Post by oldfred on 2019-12-24
Does this show if trim is running?
journalctl -u fstrim

[https://ubuntuforums.org/showthread.php?t=2386866](https://ubuntuforums.org/showthread.php?t=2386866)
the weekly fstrim has been moved from cron (anacron) to a systemd timer.service

```
fred@bionic-z97:~$ systemctl list-timers |grep fstrim
Mon 2019-12-30 00:00:00 CST  5 days left   Mon 2019-12-23 00:00:29 CST  1 day 10h ago fstrim.timer                 fstrim.service

```

But I have my own daily trim. So my daily trim log shows less trimmed one day a week.

---

