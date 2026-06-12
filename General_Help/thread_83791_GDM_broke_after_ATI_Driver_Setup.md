---
title: "GDM broke after ATI Driver Setup"
date: 2005-10-29
forum: General Help
---

### Post by kspades on 2005-10-29
Sux dont it?

Anyway...after I installed the latest ATI drivers as per the HOWTO, it seems my GDM has stopped working.  It boots to command line, I can login then type startx and it will work, but no GDM on bootup


I tried to start GDM manually and got this

$ sudo /etc/init.d/gdm start 
 * Starting GNOME Display Manager...                                     [fail]


This is what my gdm logs look like.

$ more \:0.log

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux zeus 2.6.12-9-k7 #1 Mon Oct 10 13:47:52 BST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-k7 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:47:52 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 19 02:18:00 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
SetClientVersion: 0 9
Error in "UpdateFile" -4



Whats UpdateFile -4? Does anyone know? Can anyone help?
Thanks

---

### Post by kspades on 2005-10-31
bump

---

