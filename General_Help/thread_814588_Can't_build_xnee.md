---
title: "Can't build xnee"
date: 2008-05-31
forum: General Help
---

### Post by carlwenrich on 2008-05-31
When I run ./configure I get this:

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by unutbu on 2008-05-31
1) Are you aware there is an xnee package available in the repos? (Just checking)

2) If you really do want to compile xnee, have you installed build-essential? 

3) Have you linked /bin/sh to /bin/bash?

4) Please post 

```

COLUMNS=150 dpkg --list libgtk2*

```

Perhaps you need to install libgtk2.0-dev.

---

### Post by carlwenrich on 2008-05-31
I installed 1.08-3 thru synaptic, but I downloaded the 3.02 sources from the site. Here's the output from COLUMNS=150 dpkg --list libgtk2*:

ppp@ppp-desktop:~$ COLUMNS=150 dpkg --list libgtk2*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
ii  libgtk2-perl                    1:1.161-1                       Perl interface to the 2.x series of the Gimp Toolkit library
un  libgtk2-perl-doc                <none>                          (no description available)
ii  libgtk2.0-0                     2.12.9-3ubuntu4                 The GTK+ graphical user interface library
un  libgtk2.0-0png3                 <none>                          (no description available)
ii  libgtk2.0-bin                   2.12.9-3ubuntu4                 The programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                   2.12.0-2ubuntu3                 CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                2.12.9-3ubuntu4                 Common files for the GTK+ graphical user interface library
un  libgtk2.0-data                  <none>                          (no description available)
un  libgtk2.0-dev                   <none>                          (no description available)

---

### Post by unutbu on 2008-05-31
Install libgtk2.0-dev. Here is the description:

> Description: Development files for the GTK+ library
 The GTK+ is a multi-platform toolkit for creating graphical user
 interfaces. Offering a complete set of widgets, the GTK+ is suitable
 for projects ranging from small one-off tools to complete application
 suites.
 .
** This package contains the header files and static libraries which is needed for developing the GTK+ applications**.

If you run into further trouble, you might want to consider pts 2 and 3 of my previous post.

---

### Post by carlwenrich on 2008-05-31
Ok, got it (had to install another lib). Thanks for your help.

---

### Post by unutbu on 2008-05-31
Congrats. What other lib was necessary?

---

### Post by aouie on 2008-07-23
As you try to configure the file, it should tell you what other packages are needed.
I had to install from synaptic: libpanel-applet2-dev, build-essential, libxtst-dev, and libgtk2.0-dev (this will also install several dependencies).

Sincerely,
Aouie

---

