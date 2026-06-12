---
title: "Ufraw Crashing on Precise"
date: 2013-05-01
forum: General Help
---

### Post by cscj01 on 2013-05-01
After not using UFraw for a while, I tried to open a NEF file created by my Nikon D7000 with Ufraw.  The program started to load, and then a message window popped up but disappeared too quickly for me to see, and then Ufraw terminated.  I ran Ufraw from a terminal and got the following message:```
Segmentation fault (core dumped)
```The crash report contains a core dump and some trace information, but I cannot determiine what is happening from that.  Here are a couple of parts of that crash report:

```
SegvAnalysis:
 Segfault happened at: 0x7f443a9d87e0 <cmsGetDeviceClass>:	mov    0x8(%rdi),%eax
 PC (0x7f443a9d87e0) ok
 source "0x8(%rdi)" (0x00000008) not located in a known VMA region (needed readable region)!
 destination "%eax" ok
SegvReason: reading NULL VMA
SourcePackage: ufraw
.
.
.
Title: ufraw crashed with SIGSEGV in cmsGetDeviceClass()
.
XsessionErrors:
 gnome-session[2228]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
 (metacity:3057): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed
**The aboved line repeated many times**
.
.
.
gnome-session[2228]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "xscreensaver" (No such file or directory)
 (gnome-panel:3071): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.32.3/./gobject/gsignal.c:2455: signal `size_request' is invalid for instance `0xe3f360'
 (alltray:3355): Gdk-WARNING **: Can't confine to grabbed window, not native
 (glipper:3087): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
**The above line repeated many times**
```Obviously there is much more in the report, but it's quite large, so I thought someone might get an idea from these snippets.  I can furnish the entire report if so desired.

I have been using Darktable for the last few months prior to today.  The last time I used Ufraw, which was in 12.04, it ran perfectly.  I tried removing and reinstalling Ufraw, but that did not change anything.  Darktable still opens and processes my NEF files with no problems.  Additionally, I tried older NEF files made with my D70, and Ufraw crashed with them as well.  I am running Ubuntu 12.04 x64 and Ufraw 18-1.1build1 which is what is distributed with 12.04.  Any ideas?

---

### Post by cscj01 on 2013-05-01
Well, I resolved the issue by adding the Ufraw PPA and upgrading Ufraw to version 20.0.  Still don't know why it was failing before, but I'll mark this thread as solved.

---

