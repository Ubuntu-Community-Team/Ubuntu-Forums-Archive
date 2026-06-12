---
title: "Firefox fails to start after last update"
date: 2015-09-07
forum: General Help
---

### Post by leunam12 on 2015-09-07
My system installed some updates today and Firefox crashed immediately. Since then it won't open anymore, the crash report pops up and then I have to click quit. Safe mode does the same, also creating a new .mozilla folder results in crash at startup. Thunderbird works normally.

Thanks for any assiastance

```
(process:3196): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(firefox:3196): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(firefox:3196): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(firefox:3196): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(firefox:3196): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised


```

---

### Post by patlkli on 2015-09-07
This seems to be [a permission problem]("http://ubuntuforums.org/showthread.php?t=2142601").

Please try the following and check if your user is the owner of the listed files and directories:
```
ls -al .gnome2/
```

---

### Post by leunam12 on 2015-09-07
There you go:

```
rivasdom@RivasPC-2:~$ ls -al .gnome2/
total 16
drwx------  3 rivasdom rivasdom 4096 Sep  7 09:39 .
drwxr-xr-x 79 rivasdom rivasdom 4096 Sep  7 09:40 ..
drwx------  2 rivasdom rivasdom 4096 Jun  4  2014 accels
-rw-rw-r--  1 rivasdom rivasdom   37 Jun 19 16:31 nautilus-share-modified-permissions

```

---

### Post by leunam12 on 2015-09-09
This was solved by removing the freshpepper plugin

---

