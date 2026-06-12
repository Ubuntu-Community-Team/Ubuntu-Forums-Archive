---
title: "Somewhat specific openchrome installation problem"
date: 2008-01-10
forum: General Help
---

### Post by ders on 2008-01-10
I am computer literate but new to Linux so please try to be descriptive.  I installed the Via video driver to find out it doesn't support widescreen.  I can't install openchrome now.
I have installed it before so I know it's possible.  These are the steps I took.

1) Install Via driver, then sudo apt-get remove "via driver"
2) Install openchrome from "sudo apt-get install xserver-xorg-video-openchrome"
with this result:

"The following packages have unmet dependencies:
  libxine1-x: Depends: libxvmc1 but it is not going to be installed
  xserver-xorg-video-openchrome: Depends: libviaxvmc1 (= 0.2.6+svn357-0ubuntu3) but it is not going to be installed
Depends: libviaxvmcpro1 (= 0.2.6+svn357-0ubuntu3) but it is not going to be installed"

so then I run: "apt-get -f install" with this result:
.....
"Unpacking libxvmc1 (from .../libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libXvMC.so.1', which is also in package libxvmc
Errors were encountered while processing:
 /var/cache/apt/archives/libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I have been running around in circles with this.  I have also tried to compile the driver myself which is how I did it before if I remember correctly.  Now it won't let me run the command just before "make".  its a "./something parameter"

I'm sorry this is so long.  Thanks for your help.

---

### Post by ders on 2008-01-11
I just ended up reinstalling ubuntu and installing the driver manually.  It worked like a charm.

---

