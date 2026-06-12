---
title: "Nautilus Crashed with SIGSEGV (Ubuntu 18.04.2, Unity 7)"
date: 2019-08-19
forum: General Help
---

### Post by sdsurfer on 2019-08-19
I did some searching and couldn't locate relevant threads, TYIA if you point me to them.

I have been on Ubuntu since version 16-something and have a constant recurring crash on startup across three different machines. I usually just ignore it and everything appears to work normally but obviously something is wrong. 

I have a dual boot machine (Windows 7 on second drive, almost never accessed for anything but storage,) a System 76 Gazelle lappie, and the machine I'm reporting with today is a Dell Precision 3630 Tower running 18.04.2 with the Unity 7 desktop. Aside, I have booted into Gnome a few times to see if this problem is Unity specific and as I recall it gives me the same crash (I could be incorrectly remembering, but I do recall trying that a couple times.)

The Dell is using internal dual display video, the dual boot is a dual head Nvidia card, the lappie obviously is internal video.

I always install the updates when prompted, and have dug though the man page [http://manpages.ubuntu.com/manpages/bionic/man1/nautilus.1.html.]("http://manpages.ubuntu.com/manpages/bionic/man1/nautilus.1.html")

The crash always occurs on startup/reboot:** nautilus crashed with SIGSEGV**. The nautilus version is reported as **nautilus 1:3.26.40~ubuntu18.04.4**. Further down in the crash dialogue under **SegvAnalysis** is 

```
Failure: invalid literal for int() with base 16: 'program'
```

I've used "report" several times over the last year or so but the problem doesn't appear to be going away. No sense in hammering the devs with redundant reports.

Dug through tons of logs and found the most useful information in apport.log:

```
ERROR: apport (pid 19843) Mon Aug 19 07:39:12 2019: called for pid 25182, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 19843) Mon Aug 19 07:39:12 2019: executable: /usr/bin/nautilus (command line "/usr/bin/nautilus --gapplication-service")
ERROR: apport (pid 19843) Mon Aug 19 07:39:17 2019: gdbus call error: Error connecting: Error receiving data: Connection reset by peer
ERROR: apport (pid 19843) Mon Aug 19 07:39:17 2019: debug: session gdbus call: 
ERROR: apport (pid 19843) Mon Aug 19 07:39:17 2019: wrote report /var/crash/_usr_bin_nautilus.1000.crash
```

I can provide the .crash file, not sure if it will be helpful and okay to make it public. The most relevant lines are exactly what appear in the syslog file:

```
Aug 19 06:16:55 Precision-3630-Tower nm-applet[2822]: Can't set a parent on widget which has a parent
Aug 19 06:16:55 Precision-3630-Tower nm-applet[2822]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Aug 19 06:16:55 Precision-3630-Tower nm-applet[2822]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
```

```
Aug 19 06:18:42 Precision-3630-Tower gnome-software[9554]: json_object_has_member: assertion 'member_name != NULL' failed
Aug 19 06:18:42 Precision-3630-Tower gnome-software[9554]: g_strsplit: assertion 'string != NULL' failed
Aug 19 06:18:42 Precision-3630-Tower gnome-software[9554]: g_strv_length: assertion 'str_array != NULL' failed
```

Nothing else in either the syslog or nautilus crash file seems to be an obvious issue.

I'm not sure if these entries are even relevant or where else to look, does anyone have suggestions to offer?

---

### Post by coffeecat on 2019-08-30
*Thread moved to **General Help**, and free bump!*

---

### Post by sdsurfer on 2019-09-09
Crickets! No one else has ever encountered this issue? Happened again this weekend in a reboot.

---

