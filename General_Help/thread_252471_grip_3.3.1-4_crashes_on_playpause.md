---
title: "grip 3.3.1-4 crashes on play/pause"
date: 2006-09-06
forum: General Help
---

### Post by droazen on 2006-09-06
I find that while grip works fine in terms of ripping/acting as an encoder frontend, pressing the play/pause button while a cd is in the drive causes it to immediately crash. If I launch it from the terminal, I get the following message during the crash:

```

(grip:10689): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

```

There is an [open bug]("https://launchpad.net/distros/ubuntu/+source/grip/+bug/41601") about this over at launchpad, which is marked as "needs info". I've added a short comment to the bug report confirming the original submitter's description of the problem, but apparently it's not a universal problem. Has anyone here experienced this crash with the Dapper version of grip? If so, maybe we can figure out what we have in common in terms of hardware/software configuration & update the bug report with that information.

Thanks,
David

---

### Post by claypole on 2006-11-30
I have the same problem, but it happens when I start grip in Edgy.  If I completely remove and reinstall this sometimes fixes it for a while and then it starts crashing again ](*,)

---

### Post by claypole on 2006-11-30
Had a look at launchpad and it looks like I've fixed it by changing play-on-insert from 1 to 0 in ~/.grip :)

---

