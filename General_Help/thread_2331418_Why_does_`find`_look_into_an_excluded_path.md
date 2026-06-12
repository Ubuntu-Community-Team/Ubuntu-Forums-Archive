---
title: "Why does `find` look into an excluded path?"
date: 2016-07-22
forum: General Help
---

### Post by vasa1 on 2016-07-22
I have this alias:```
alias 1d='find ~/ \
! -path "/home/vasa1/.config/kupfer/*" \
! -path "/home/vasa1/.mozilla/*" \
! -path "/home/vasa1/.cache/*" \
! -path "/home/vasa1/.config/geany/*" \
! -path "/home/vasa1/.config/google-chrome/*" \
! -path "/home/vasa1/.config/leafpad/*" \
! -path "/home/vasa1/.config/libfm/*" \
! -path "/home/vasa1/.config/pcmanfm/*" \
! -path "/home/vasa1/.config/Thunar/*" \
! -path "/home/vasa1/.config/dconf/*" \
! -path "/home/vasa1/.config/gedit/*" \
! -path "/home/vasa1/.config/Mousepad/*" \
! -path "/home/vasa1/.config/mirage/*" \
! -path "/home/vasa1/.config/xfce4/*" \
! -path "/home/vasa1/.dbus/*" \
! -path "/home/vasa1/.mpv/*" \
! -path "/home/vasa1/.local/share/Trash/*" \
! -path "/home/vasa1/.config/libreoffice/4/user/*" \
! -path "/home/vasa1/.dropbox/*" \
! -name "recently-used.xbel" \
! -path "/home/vasa1/Public/Backups/*" \
! -path "/home/vasa1/.local/share/gvfs-metadata/*" \
! -path "/home/vasa1/.xsession-errors*" \
! -path "/home/vasa1/.tint2-crash.log" \
-mtime -1 -type f -ls'
```But the first line on running that alias is always as shown below```
11:57 AM ~ $ 1d
find: ‘/home/vasa1/.cache/dconf’: Permission denied
  7209307      8 -rw-------   1 vasa1    vasa1        5069 Jul 22 11:53 /home/vasa1/.bash_aliases
  7209061      4 -rw-rw-r--   1 vasa1    vasa1        1099 Jul 22 11:51 /home/vasa1/.config/mimeapps.list
  7209083     12 -rw-rw-r--   1 vasa1    vasa1        8683 Jul 22 06:11 /home/vasa1/Desktop/mseb-daily.ods
  7733444      4 -rw-r--r--   1 vasa1    vasa1        1580 Jul 21 20:43 /home/vasa1/.local/share/applications/libreoffice-math.desktop
  7208967      4 -rw-------   1 vasa1    vasa1          64 Jul 22 05:16 /home/vasa1/.Xauthority
  8258012     16 -rw-rw-r--   1 vasa1    vasa1       10677 Jul 21 16:19 /home/vasa1/Dropbox/CurrSoc/MCM/20160723-mcm-agenda.odt
  7733472     12 -rw-rw-r--   1 vasa1    vasa1        4695 Jul 22 06:09 /home/vasa1/Dropbox/_MyMkd/find.mkd
  7213648     64 -rw-------   1 vasa1    vasa1       65454 Jul 22 10:34 /home/vasa1/.bash_history
11:57 AM ~ $ 

```Why do I see ```
find: ‘/home/vasa1/.cache/dconf’: Permission denied

```as the first line in the output?

---

### Post by steeldriver on 2016-07-22
I think it's because it still needs to test everything it finds against the path pattern - if you want to ignore a whole directory branch completely, use -prune instead e.g.

```

$ find ~/ ! -path "/home/steeldriver/.cache/*" -mtime -1 -print
/home/steeldriver/
/home/steeldriver/.cache
 [COLOR=#ff0000]find: ‘/home/steeldriver/.cache/dconf’: Permission denied[/COLOR]
/home/steeldriver/.Xauthority
/home/steeldriver/somefile
/home/steeldriver/.config/dconf
/home/steeldriver/.config/dconf/user
/home/steeldriver/.local/share/zeitgeist/activity.sqlite-shm
/home/steeldriver/.local/share/zeitgeist/activity.sqlite-wal
/home/steeldriver/.lesshst

```

whereas
```

$ find ~/ -path "/home/steeldriver/.cache" -prune -o -mtime -1 -print
/home/steeldriver/
/home/steeldriver/.Xauthority
/home/steeldriver/somefile
/home/steeldriver/.config/dconf
/home/steeldriver/.config/dconf/user
/home/steeldriver/.local/share/zeitgeist/activity.sqlite-shm
/home/steeldriver/.local/share/zeitgeist/activity.sqlite-wal
/home/steeldriver/.lesshst

```

If you want to prune multiple dirs you can do so by grouping them with OR conditions

```

$ find ~/ \( \
  -path ~/.cache -o \
  -path ~/.config -o \
  -path ~/.local \
  \) -prune -o -mtime -1 -print
/home/steeldriver/
/home/steeldriver/.Xauthority
/home/steeldriver/somefile
/home/steeldriver/.lesshst

```

---

### Post by vasa1 on 2016-07-22
Thanks for "-prune". Marking this [SOLVED].

---

### Post by mc4man on 2016-07-22
That file/folder shouldn't even exist, usually from running something as root that you shouldn't. (.cache/dconf/

---

### Post by vasa1 on 2016-07-22
> **mc4man said:**
> That file/folder shouldn't even exist, usually from running something as root that you shouldn't. (.cache/dconf/
That folder and the single 2-byte file "user" within it was created on 2016-04-20. Owned by root. I don't know how it got there very :confused:

I haven't run anything with gksudo or sudo -H or pkexec for quite a long time.

---

### Post by mc4man on 2016-07-22
> **vasa1 said:**
> That folder and the single 2-byte file "user" within it was created on 2016-04-20. Owned by root. I don't know how it got there very :confused:

I haven't run anything with gksudo or sudo -H or pkexec for quite a long time.
In an ubuntu session i'm pretty sure something like sudo gedit will create the file. (gksudo or sudo -H or pkexec are acceptable actions & wouldn't cause
In any event feel free to delete the .cache/dconf folder (as root

---

### Post by vasa1 on 2016-07-22
> **mc4man said:**
> In an ubuntu session i'm pretty sure something like sudo gedit will create the file. (gksudo or sudo -H or pkexec are acceptable actions & wouldn't cause
In any event feel free to delete the .cache/dconf folder (as rootWill do (and keep a lookout for its re-appearance). Thanks!

---

