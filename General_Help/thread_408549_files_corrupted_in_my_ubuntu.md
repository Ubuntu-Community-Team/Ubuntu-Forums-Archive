---
title: "files corrupted in my ubuntu?"
date: 2007-04-13
forum: General Help
---

### Post by leo1981 on 2007-04-13
hi,
I had strange problems lately with feisty beta.
I updated from 6.10 to 7.04 easily, it works for several days, with reboots and updates.
I didn't do anything funny, and I use official repositories.
Two days ago, I received a login error:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "leo"
Impossible to write wtmp
```

I edited Default making it reads wtmp.1 (the backup). Gnome started, but I notice this:
```

ls -s /var/log/wtmp
?r-sr----x 8202 1952674405 1920299877 1651076128 2034-07-26 17:06 /var/log/wtmp
```

Then I tried to upgrade my system, and I got this:
```
dpkg: failed to open diversions file. No device or address
```
I checked diversion files, I got this:
```
leo@leo:/var/lib/dpkg$ ls -l div*
br-xr-xrwt 26996 537554017 538995060   97, 109 2029-03-26 03:14 diversions
?--xr-S-wx  8300 537555567 538992995 538970745 2021-08-21 05:01 diversions-old
```

Is it normal? How can I fix that?
Thank you.

Leonardo

---

