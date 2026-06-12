---
title: "[SOLVED] Broken software sources"
date: 2008-06-04
forum: General Help
---

### Post by tdwester on 2008-06-04
It looks like I broke my software sources, I now get this error E: Type '*' is not known on line 57 in source list /etc/apt/sources.list
E: Unable to lock the list directory.

---

### Post by drs305 on 2008-06-04
Open and take a look at line 57 of your /etc/apt/sources.list or post the results here so we can see it:

To edit:
```
gksudo gedit /etc/apt/sources.list
```

To list:
```
cat /etc/apt/sources.list
```

It appears your sources.list is fairly large. To view only the uncommented lines:
```
cat  /etc/apt/sources.list | grep -v "#"
```

---

### Post by tdwester on 2008-06-04
here is line 57  * mono-jay LALR(1) parser generator oriented to Java/CLI 

* libmono-npgsql1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (64.8 KiB)

    * libmono-npgsql2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (64.9 KiB)

    * libmono-oracle1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (52.1 KiB)

    * libmono-oracle2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (52.3 KiB)

    * libmono-peapi1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (43.0 KiB)

    * libmono-peapi2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (43.1 KiB)

    * libmono-relaxng1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (81.3 KiB)

    * libmono-relaxng2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (81.8 KiB)

    * libmono-security1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (112.2 KiB)

    * libmono-security2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (113.0 KiB)

    * libmono-sharpzip0.6-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (47.4 KiB)

    * libmono-sharpzip0.84-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (57.2 KiB)

    * libmono-sharpzip2.6-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (47.5 KiB)

    * libmono-sharpzip2.84-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (57.2 KiB)

    * libmono-sqlite1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (33.8 KiB)

    * libmono-sqlite2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (65.7 KiB)

    * libmono-system-data1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (218.4 KiB)

    * libmono-system-data2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (284.1 KiB)

    * libmono-system-ldap1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (18.8 KiB)

    * libmono-system-ldap2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (18.8 KiB)

    * libmono-system-messaging1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (26.7 KiB)

    * libmono-system-messaging2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (26.7 KiB)

    * libmono-system-runtime1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (59.5 KiB)

    * libmono-system-runtime2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (68.0 KiB)

    * libmono-system-web1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (388.0 KiB)

    * libmono-system-web2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (789.2 KiB)

    * libmono-system1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (882.4 KiB)

    * libmono-system2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (1.3 MiB)

    * libmono-system2.1-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (235.1 KiB)

    * libmono-winforms1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (877.8 KiB)

    * libmono-winforms2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (1.2 MiB)

    * libmono0-dbg_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (1.7 MiB)

    * libmono0-dbg_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (1.6 MiB)

    * libmono0-dbg_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (1.8 MiB)

    * libmono0_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (904.3 KiB)

    * libmono0_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (858.4 KiB)

    * libmono0_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (855.0 KiB)

    * libmono1.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (365.3 KiB)

    * libmono2.0-cil_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (208.5 KiB)

    * mono-1.0-devel_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (355.3 KiB)

    * mono-1.0-service_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (9.0 KiB)

    * mono-2.0-devel_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (181.3 KiB)

    * mono-2.0-service_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (9.0 KiB)

    * mono-common_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (112.2 KiB)

    * mono-common_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (111.0 KiB)

    * mono-common_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (111.4 KiB)

    * mono-dbg_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (11.3 MiB)

    * mono-gac_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (14.0 KiB)

    * mono-gmcs_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (349.0 KiB)

    * mono-jay_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (68.2 KiB)

    * mono-jay_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (62.4 KiB)

    * mono-jay_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (62.9 KiB)

    * mono-jit-dbg_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (1.6 MiB)

    * mono-jit-dbg_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (1.5 MiB)

    * mono-jit-dbg_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (1.7 MiB)

    * mono-jit_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (800.2 KiB)

    * mono-jit_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (740.3 KiB)

    * mono-jit_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (745.9 KiB)

    * mono-mcs_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (316.2 KiB)

    * mono-mjs_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (8.2 KiB)

    * mono-runtime_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (24.8 KiB)

    * mono-runtime_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (24.7 KiB)

    * mono-runtime_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (24.8 KiB)

    * mono-smcs_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (336.8 KiB)

    * mono-utils_1.2.6+dfsg-6ubuntu3~gutsy0_amd64.deb (645.0 KiB)

    * mono-utils_1.2.6+dfsg-6ubuntu3~gutsy0_i386.deb (607.8 KiB)

    * mono-utils_1.2.6+dfsg-6ubuntu3~gutsy0_lpia.deb (606.0 KiB)

    * mono-xbuild_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (23.4 KiB)

    * mono_1.2.6+dfsg-6ubuntu3~gutsy0.diff.gz (64.8 KiB)

    * mono_1.2.6+dfsg-6ubuntu3~gutsy0.dsc (2.8 KiB)

    * mono_1.2.6+dfsg.orig.tar.gz (22.2 MiB)

    * prj2make-sharp_1.2.6+dfsg-6ubuntu3~gutsy0_all.deb (18.6 KiB)

Show files mono-addins - 0.3.1-4~gutsy0 		hyperair 	2008-03-29 	Published 	Gutsy 	Libs 	Built successfully
Publishing details

    * Published on 2008-03-29

Changelog

mono-addins (0.3.1-4~gutsy0) gutsy; urgency=low

  * Backport to Gutsy

 -- Chow Loong Jin <email address hidden>   Sun, 30 Mar 2008 04:54:03 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * libmono-addins-gui0.2-cil GTK# frontend library for Mono.Addins

    * libmono-addins0.2-cil addin framework for extensible CLI applications/libraries

Download files from Librarian

    * libmono-addins-gui0.2-cil_0.3.1-4~gutsy0_all.deb (43.3 KiB)

    * libmono-addins0.2-cil_0.3.1-4~gutsy0_all.deb (110.9 KiB)

    * mono-addins_0.3.1-4~gutsy0.diff.gz (12.0 KiB)

    * mono-addins_0.3.1-4~gutsy0.dsc (1.2 KiB)

    * mono-addins_0.3.1.orig.tar.gz (229.0 KiB)

Show files mono-zeroconf - 0.7.3-1~gutsy0 		hyperair 	2008-03-31 	Published 	Gutsy 	Libs 	Built successfully
Publishing details

    * Published on 2008-03-31

Changelog

mono-zeroconf (0.7.3-1~gutsy0) gutsy; urgency=low

  * Backport to Gutsy

 -- Chow Loong Jin <email address hidden>   Mon, 31 Mar 2008 19:43:36 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * libmono-zeroconf1.0-cil CLI library for multicast DNS service discovery

    * monodoc-mono-zeroconf-manual compiled XML documentation for mono-zeroconf

    * mzclient CLI library for multicast DNS service discovery (commandline tool)

Download files from Librarian

    * libmono-zeroconf1.0-cil_0.7.3-1~gutsy0_all.deb (18.4 KiB)

    * mono-zeroconf_0.7.3-1~gutsy0.diff.gz (3.3 KiB)

    * mono-zeroconf_0.7.3-1~gutsy0.dsc (1.0 KiB)

    * mono-zeroconf_0.7.3.orig.tar.gz (119.4 KiB)

    * monodoc-mono-zeroconf-manual_0.7.3-1~gutsy0_all.deb (15.0 KiB)

    * mzclient_0.7.3-1~gutsy0_all.deb (8.1 KiB)

Show files ndesk-dbus - 0.6.0-1~gutsy0 		hyperair 	2008-03-29 	Published 	Gutsy 	Devel 	Built successfully
Publishing details

    * Published on 2008-03-29

Changelog

ndesk-dbus (0.6.0-1~gutsy0) gutsy; urgency=low

  * Backport to Gutsy

 -- Chow Loong Jin <email address hidden>   Sun, 30 Mar 2008 04:45:50 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * libndesk-dbus1.0-cil CLI implementation of D-Bus

Download files from Librarian

    * libndesk-dbus1.0-cil_0.6.0-1~gutsy0_all.deb (55.7 KiB)

    * ndesk-dbus_0.6.0-1~gutsy0.diff.gz (2.6 KiB)

    * ndesk-dbus_0.6.0-1~gutsy0.dsc (904 bytes)

    * ndesk-dbus_0.6.0.orig.tar.gz (119.4 KiB)

Show files ndesk-dbus-glib - 0.4.1-1~gutsy0 		hyperair 	2008-03-29 	Published 	Gutsy 	Devel 	Built successfully
Publishing details

    * Published on 2008-03-29

Changelog

ndesk-dbus-glib (0.4.1-1~gutsy0) gutsy; urgency=low

  * Backport to Gutsy

 -- Chow Loong Jin <email address hidden>   Sun, 30 Mar 2008 05:20:15 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * libndesk-dbus-glib1.0-cil CLI implementation of D-Bus (GLib mainloop integration)

Download files from Librarian

    * libndesk-dbus-glib1.0-cil_0.4.1-1~gutsy0_all.deb (7.8 KiB)

    * ndesk-dbus-glib_0.4.1-1~gutsy0.diff.gz (2.8 KiB)

    * ndesk-dbus-glib_0.4.1-1~gutsy0.dsc (970 bytes)

    * ndesk-dbus-glib_0.4.1.orig.tar.gz (83.5 KiB)

Show files njb-sharp - 0.3.0-2ubuntu0~gutsy1 		hyperair 	2008-04-14 	Published 	Gutsy 	Libs 	Built successfully
Publishing details

    * Published on 2008-04-14

Changelog

njb-sharp (0.3.0-2ubuntu0~gutsy1) gutsy; urgency=low

  * Bump the version up to meet banshee's build-deps

 -- Chow Loong Jin <email address hidden>   Mon, 14 Apr 2008 17:06:40 +0800

Builds

    * [FULLYBUILT] amd64
    * [FULLYBUILT] i386
    * [FULLYBUILT] lpia

Built Packages

    * libnjb-cil CLI binding for libnjb

    * monodoc-njb-manual compiled XML documentation for njb-sharp

Download files from Librarian

    * libnjb-cil_0.3.0-2ubuntu0~gutsy1_amd64.deb (17.6 KiB)

    * libnjb-cil_0.3.0-2ubuntu0~gutsy1_i386.deb (17.5 KiB)

    * libnjb-cil_0.3.0-2ubuntu0~gutsy1_lpia.deb (17.4 KiB)

    * monodoc-njb-manual_0.3.0-2ubuntu0~gutsy1_all.deb (15.3 KiB)

    * njb-sharp_0.3.0-2ubuntu0~gutsy1.diff.gz (3.1 KiB)

    * njb-sharp_0.3.0-2ubuntu0~gutsy1.dsc (840 bytes)

    * njb-sharp_0.3.0.orig.tar.gz (310.4 KiB)

Show files notify-sharp - 0.4.0~r2998-1~hardy1 		hyperair 	2008-04-11 	Published 	Hardy 	Libs 	Built successfully
Publishing details

    * Published on 2008-04-11

Changelog

notify-sharp (0.4.0~r2998-1~hardy1) hardy; urgency=low

  * Zero-change backport

 -- Chow Loong Jin <email address hidden>   Fri, 11 Apr 2008 19:34:54 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * libnotify0.4-cil CLI library for desktop notifications

    * monodoc-notify-sharp-manual compiled XML documentation for notify-sharp

Download files from Librarian

    * libnotify0.4-cil_0.4.0~r2998-1~hardy1_all.deb (8.9 KiB)

    * monodoc-notify-sharp-manual_0.4.0~r2998-1~hardy1_all.deb (6.8 KiB)

    * notify-sharp_0.4.0~r2998-1~hardy1.diff.gz (2.6 KiB)

    * notify-sharp_0.4.0~r2998-1~hardy1.dsc (1.1 KiB)

    * notify-sharp_0.4.0~r2998.orig.tar.gz (91.3 KiB)

Show files notify-sharp - 0.4.0~r2998-1~gutsy1 		hyperair 	2008-04-11 	Published 	Gutsy 	Libs 	Built successfully
Publishing details

    * Published on 2008-04-11

Changelog

notify-sharp (0.4.0~r2998-1~gutsy1) gutsy; urgency=low

  * Zero-change backport

 -- Chow Loong Jin <email address hidden>   Fri, 11 Apr 2008 19:34:15 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * libnotify0.4-cil CLI library for desktop notifications

    * monodoc-notify-sharp-manual compiled XML documentation for notify-sharp

Download files from Librarian

    * libnotify0.4-cil_0.4.0~r2998-1~gutsy1_all.deb (8.9 KiB)

    * monodoc-notify-sharp-manual_0.4.0~r2998-1~gutsy1_all.deb (6.8 KiB)

    * notify-sharp_0.4.0~r2998-1~gutsy1.diff.gz (2.6 KiB)

    * notify-sharp_0.4.0~r2998-1~gutsy1.dsc (1.1 KiB)

    * notify-sharp_0.4.0~r2998.orig.tar.gz (91.3 KiB)

Show files podsleuth - 0.6.1-1~gutsy1 		hyperair 	2008-04-13 	Published 	Gutsy 	Sound 	Built successfully
Publishing details

    * Published on 2008-04-13

Changelog

podsleuth (0.6.1-1~gutsy1) gutsy; urgency=low

  * Backport to Gutsy

 -- Chow Loong Jin <email address hidden>   Mon, 14 Apr 2008 00:21:34 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * podsleuth Tool to discover detailed information about Apple iPods

Download files from Librarian

    * podsleuth_0.6.1-1~gutsy1.diff.gz (2.0 KiB)

    * podsleuth_0.6.1-1~gutsy1.dsc (856 bytes)

    * podsleuth_0.6.1-1~gutsy1_all.deb (49.8 KiB)

    * podsleuth_0.6.1.orig.tar.gz (132.1 KiB)

Show files taglib-sharp - 2.0.3.0-1~gutsy0 		hyperair 	2008-04-04 	Published 	Gutsy 	Libs 	Built successfully
Publishing details

    * Published on 2008-04-04

Changelog

taglib-sharp (2.0.3.0-1~gutsy0) gutsy; urgency=low

  * Backport to Gutsy

 -- Chow Loong Jin <email address hidden>   Fri, 04 Apr 2008 19:42:21 +0800

Builds

    * [FULLYBUILT] i386

Built Packages

    * libtaglib2.0-cil CLI library for accessing audio and video files metadata

    * monodoc-taglib-manual compiled XML documentation for taglib-sharp

Download files from Librarian

    * libtaglib2.0-cil_2.0.3.0-1~gutsy0_all.deb (135.4 KiB)

    * monodoc-taglib-manual_2.0.3.0-1~gutsy0_all.deb (267.6 KiB)

    * taglib-sharp_2.0.3.0-1~gutsy0.diff.gz (5.6 KiB)

    * taglib-sharp_2.0.3.0-1~gutsy0.dsc (936 bytes)

    * taglib-sharp_2.0.3.0.orig.tar.gz (344.2 KiB)

Actions

    * View PPA
    * View build records

PPA supported series

    * 8.10 "Intrepid" - development
          o amd64 (official)
          o i386 (official)
          o lpia (official)
    * 8.04 "Hardy" - current
          o amd64 (official)
          o i386 (official)
          o lpia (official)
    * 7.10 "Gutsy" - supported
          o amd64 (official)
          o i386 (official)
          o lpia
    * 7.04 "Feisty" - supported
          o amd64 (official)
          o i386 (official)
    * 6.06 "Dapper" - supported
          o amd64 (official)
          o i386 (official)
todd@todd-desktop:~$

---

### Post by drs305 on 2008-06-04
Something seriously messed up your sources.list  Don't worry, it's not hard to fix but I'm in Hardy so I cannot give you an example of a current sources.list. 

The list contains gutsy references - is that what you are currently running?

Someone with a gutsy sources.list can post a good copy of their sources.list here. In the meantime I will look around and see if I can find a recent one.

You might want to start by making a copy of your current sources.list. My suggestion is "/etc/apt/sources.list.bad" ;-)

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bad
```

---

### Post by tdwester on 2008-06-04
After I deleted all the crap with a * it seems to be working fine now.

---

### Post by tdwester on 2008-06-04
I was just trying to add the new banshee RC to my sources list and it went boom! Oh well if I break it I get to keep both halves.

---

### Post by drs305 on 2008-06-04
> **tdwester said:**
> I was just trying to add the new banshee RC to my sources list and it went boom! Oh well if I break it I get to keep both halves.

Yeah, well bytes are cheap these days. :)

Please mark this solved if you have no further questions.

---

