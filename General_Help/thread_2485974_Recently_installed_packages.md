---
title: "Recently installed packages?"
date: 2023-04-15
forum: General Help
---

### Post by stevermann on 2023-04-15
I need to restore my Ubuntu from a backup- is there an easy way to see what packages have been installed in the past two weeks?

---

### Post by TheFu on 2023-04-16
> **stevermann said:**
> I need to restore my Ubuntu from a backup- is there an easy way to see what packages have been installed in the past two weeks?

I don't know, but would guess the .deb files would have a data-stamp within that period.  Those are cached somewhere under /var/cache/apt/archives/
You could use **ls** sorted by date or **find** to get a list.

I see that these packages were updated since April 1 on a system here:
```
tzdata_2023c-0ubuntu0.22.04.0_all.deb
python3-louis_3.20.0-2ubuntu0.2_all.deb
liblouis20_3.20.0-2ubuntu0.2_amd64.deb
liblouis-data_3.20.0-2ubuntu0.2_all.deb
sudo_1.9.9-1ubuntu2.4_amd64.deb
firefox-locale-en_112.0+linuxmint1+vera_amd64.deb
firefox_112.0+linuxmint1+vera_amd64.deb
mintupdate_5.9.8_all.deb
thunderbird-locale-en_1%3a102.10.0+build2-0ubuntu0.22.04.1_amd64.deb
thunderbird-locale-en-us_1%3a102.10.0+build2-0ubuntu0.22.04.1_all.deb
thunderbird_1%3a102.10.0+build2-0ubuntu0.22.04.1_amd64.deb
thunderbird-gnome-support_1%3a102.10.0+build2-0ubuntu0.22.04.1_amd64.deb
libgs9-common_9.55.0~dfsg1-0ubuntu5.2_all.deb
libgs9_9.55.0~dfsg1-0ubuntu5.2_amd64.deb
ghostscript-x_9.55.0~dfsg1-0ubuntu5.2_amd64.deb
ghostscript_9.55.0~dfsg1-0ubuntu5.2_amd64.deb
python3-problem-report_2.20.11-0ubuntu82.4_all.deb
python3-apport_2.20.11-0ubuntu82.4_all.deb
```
And no snap packages will show up either.

You can probably look through the APT logs. /var/log/apt/ I bet there's a timestamp for each action taken inside those files too. Probably easier to read. Yep.
```
$ egrep Start-Date *
history.log:Start-Date: 2023-04-01  08:29:05
history.log:Start-Date: 2023-04-04  09:17:03
history.log:Start-Date: 2023-04-06  18:18:31
history.log:Start-Date: 2023-04-08  09:37:24
history.log:Start-Date: 2023-04-09  09:37:24
history.log:Start-Date: 2023-04-09  09:38:13
history.log:Start-Date: 2023-04-15  08:54:04
```

---

### Post by Impavidus on 2023-04-17
You can check /var/log/dpkg.log. Last month's log will be at /var/log/dpkg.log.1.

---

### Post by MAFoElffen on 2023-04-19
To roll back updates and update problems, I look at these 3 log files:
/var/log/apt/history
/var/log/apt/term.log
/var/log/dpkg.log

In history.log, in the date range (Started/Ended), the records you are concerned with are the ones that start with "Unpacking" in Field1, Field2 is the package name. Field3 is the new version. If it is not new, but updating something older, then Feild4 is "over" and Field5 is the old version number.

---

