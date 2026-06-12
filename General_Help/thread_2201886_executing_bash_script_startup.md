---
title: "executing bash script startup"
date: 2014-01-26
forum: General Help
---

### Post by pjmlmas on 2014-01-26
I have bash script that tar and zip home to exthd. I would like this to occur whenever I log in. I see conflicting advice on different forums.  I need to mount exthd or check if it is mounted, then tar and zip to exthd. I thought init.d but maybe not? P.S. How to mount and check and throw error message that will be picked up/ noticed if exthd is disconnected?

---

### Post by Lars Noodén on 2014-01-26
As far as getting the script to run when you do a graphical login, then that would be [.xinitrc](https://wiki.ubuntu.com/CustomXSession#How_to_create_a_X_session_script).  

About identifying the external drive, that would best be done by UUID, but a method eludes me at the moment.

---

### Post by Lars Noodén on 2014-01-26
The directory /dev/disk/by-uuid/ contains a list of all mounted partitions, identified by UUID.

```

uuid=ddc25bdf-ce67-419a-b3b9-6c524211ecba
find /dev/disk/by-uuid/ -type l | grep ${uuid} && echo ok || echo fail

```

---

### Post by ian-weisser on 2014-01-27
You can do an Upstart-udev job that launches your backup script whenever the exthd (and only the exthd)  is plugged in.
If you want to limit backups to once each day, it's not difficult - a timestamp file checked by your script logic.
See [http://upstart.ubuntu.com/cookbook/#upstart-udev-bridge](http://upstart.ubuntu.com/cookbook/#upstart-udev-bridge)

---

