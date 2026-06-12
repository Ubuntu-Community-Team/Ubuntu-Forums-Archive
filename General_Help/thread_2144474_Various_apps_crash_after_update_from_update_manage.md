---
title: "Various apps crash after update from update manager. 1204"
date: 2013-05-12
forum: General Help
---

### Post by knuthalvor on 2013-05-12
Hello, after I allowed an update from the update manager various
applications have been crashing. This is the log from the update from /var/log/apt:

Start-Date: 2013-05-10  10:31:09
Commandline: aptdaemon role='role-commit-packages' sender=':1.1882'
Upgrade: libdrm-intel1:i386 (2.4.39-0ubuntu0.2, 2.4.43-0ubuntu0.0.1), libdrm2:i386 (2.4.39-0ubuntu0.2, 2.4.43-0ubuntu0.0.1), libdrm-nouveau1a:i386 (2.4.39-0ubuntu0.2, 2.4.43-0ubuntu0.0.1), telepathy-idle:i386 (0.1.11-2, 0.1.11-2ubuntu0.1), alsa-utils:i386 (1.0.25-1ubuntu5, 1.0.25-1ubuntu5.2), libasound2:i386 (1.0.25-1ubuntu10.1, 1.0.25-1ubuntu10.2), libdrm-radeon1:i386 (2.4.39-0ubuntu0.2, 2.4.43-0ubuntu0.0.1)
End-Date: 2013-05-10  10:32:08

The applications i have been having the most trouble with are Totem, firefox and chromium, but it applies to other similar apps aswell. Command line programs like the moc music player work fine.
Here is the output from a totem crash:

knut:Videos$ totem Veep\ -\ The\ Complete\ Season\ 1\ \[HDTV\]/Veep.S01E05.HDTV.x264-ASAP.mp4 

(totem:3996): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'


(totem:3996): GLib-GObject-WARNING **: type name `ffenc_pgm0CGM (Poqgable GCpyMap) K~age' contains invalid characters

(totem:3996): GLib-GObject-CRITICAL **: g_type_set_qdata: assertion `node != NULL' failed

(totem:3996): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(totem:3996): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(totem:3996): GLib-GObject-WARNING **: type name `ffdec_pgm0CGM_(Poqgable_GCpyMap)_K~age' contains invalid characters

(totem:3996): GLib-GObject-CRITICAL **: g_type_set_qdata: assertion `node != NULL' failed

(totem:3996): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

** (totem:3996): WARNING **: Failed to register ffdec_pgm0CGM_(Poqgable_GCpyMap)_K~age
Segmentation fault (core dumped)

Other crashes look similar.

I am a casuall user of Ubuntu and am not well versed in the technical stuff,  so this may well be something rather obvious.
I have installed Ubuntu 1204lts and have been accepting the poput updates from the update manager without really looking very closely at them. Here is some information about my system that i don't know if is relevant or not:
Ubuntu:
release 12.04(precise) 32-bit
Kernel Linux 3.2.0-41-generic-pae
GNOME 3.4.2

processor Intel Pentium(R)Dual CPU T2370 @ 1.73GHz x 2


Hope you can help me,
regards

---

