---
title: "[SOLVED] Problem with archive manager on Xubuntu"
date: 2013-03-17
forum: General Help
---

### Post by mr.suchy on 2013-03-17
Hi,

I have simple problem with archive manager. When I select a file and click "unrar here" in menu I have error in log:
File: apport.log
```

RROR: apport (pid 4215) Sun Mar 17 22:43:14 2013: called for pid 4210, signal 6, core limit 0
ERROR: apport (pid 4215) Sun Mar 17 22:43:14 2013: executable: /usr/bin/file-roller (command line "file-roller --extract-to=/home/mrsuchy/Pobrane --extract-here --force /home/mrsuchy/Pobrane/spam-free-wordpress.zip")
ERROR: apport (pid 4215) Sun Mar 17 22:43:14 2013: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


```

What can I do with this issue ?

Best regards !

---

### Post by Toz on 2013-03-17
Sounds like it may be the file-roller bug. Have a look here for more info: [http://ubuntuforums.org/showthread.php?t=2083870]("http://ubuntuforums.org/showthread.php?t=2083870")

---

### Post by mr.suchy on 2013-03-18
Good to know I try this later. Generally, the solution install peazip_4.9.LINUX.Qt-2_i386.deb or modify the file-roller config

```

I fixed it by changing corresponding command in the gnome-file-roller.tap file. In my case this file has been placed at 

/usr/lib/i386-linux-gnu/thunar-archive-plugin/gnome-file-roller.tap   Just edit it replacing this line:
  
file-roller "--extract-to=$(pwd)" --extract-here --force "$@"    with this one:
  
file-roller --extract-here --force "$@"

```
I give a try. Thanks for help.

---

