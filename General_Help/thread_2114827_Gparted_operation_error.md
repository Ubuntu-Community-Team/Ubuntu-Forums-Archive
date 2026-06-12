---
title: "Gparted operation error"
date: 2013-02-11
forum: General Help
---

### Post by sinaphysics on 2013-02-11
When I want to open Gparted :
> sudo gparted


The result is disappointing. 

> 
(process:12516): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
======================
libparted : 2.3
======================
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(gpartedbin:12516): glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: locale::facet::_S_create_c_locale name not valid


How you find this ?

---

### Post by dino99 on 2013-02-11
*********Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.     ***********

so .font.conf should have been removed (now its replaced by the folders .fontconfig & fontconfig)

As you dont tell us which ubuntu is used, its hard to help you more. Is the libparted0-i18n installed ? and the farsi packages ?

- its better to use gparted from a livecd/usb, and always with unmounted partition

sudo dpkg-reconfigure  fontconfig

---

### Post by ajgreeny on 2013-02-11
Don't forget you should always use gksudo (gnome/gtk) oe kdesu (kde) not sudo for graphical applications.  See **RootSudo** in my signature for details of why and potential problems if you don't

---

### Post by Mark Phelps on 2013-02-11
> **sinaphysics said:**
> When I want to open Gparted :


The result is disappointing. 



How you find this ?
Have you tried using the Dash, and Applications and selecting it from there?

---

### Post by Bufeu on 2013-02-11
Open GParted with *gksudo gparted* instead.

---

### Post by sinaphysics on 2013-02-12
I should clarify which I'm using Ubuntu 12.10 with Gnome shell. And I use Farsi TTF, I've not installed any Farsi package( I mean "deb").  In continuous I don't know about "libparted0-i18n" :( 
I tried "gksudo gparted" and that dowsn't work too. In addition I have same problem with Goldendict app as well. I should add this, I have put two Farsi font in ~/.fonts folder too.

---

### Post by offgridguy on 2013-02-12
Unless you only want to look at your partition table, it is better to use the live
version of gparted, CD/ USB, to do any actual editing.

---

### Post by ACubed10 on 2013-02-12
well I can honestly tell you when I had 12.10 install on my computer, I couldn't get gparted to even format a flash drive.  It gave me errors all over the place.  So I backed up all my files, did a fresh install on 12.04 and its working great!  Could run gparted without error to format my flash drive.  Guess I'll be sticking with the LTS's for now

---

### Post by offgridguy on 2013-02-13
> **ACubed10 said:**
> well I can honestly tell you when I had 12.10 install on my computer, I couldn't get gparted to even format a flash drive.  It gave me errors all over the place.  So I backed up all my files, did a fresh install on 12.04 and its working great!  Could run gparted without error to format my flash drive.  Guess I'll be sticking with the LTS's for now
Good choice.:D

---

