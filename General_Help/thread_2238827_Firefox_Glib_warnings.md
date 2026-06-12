---
title: "Firefox Glib warnings"
date: 2014-08-10
forum: General Help
---

### Post by mayagrafix on 2014-08-10
When I run Firefox from a terminal these messages appear:
> (process:27607): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(firefox:27607): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(firefox:27607): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(firefox:27607): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(firefox:27607): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
The program runs fine otherwise, just wandering if there is something broken that needs fixing :<)

Thanks for any help--

---

### Post by vasa1 on 2014-08-10
> **mayagrafix said:**
> When I run Firefox from a terminal these messages appear:

The program runs fine otherwise, just wandering if there is something broken that needs fixing :<)

Thanks for any help--
[http://askubuntu.com/a/422400](http://askubuntu.com/a/422400)

---

### Post by mayagrafix on 2014-08-10
> The messages you see being printed to the console are not necessarily errors. Most of the ones in your screen shots are in fact, just informative, or warnings. The warnings about theme handling, are due to the GTK+ theme you are using. They are not fatal, but they do need to be fixed by whomever made the theme, and they may in the future cause greater issues if they do not get fixed

Thanks for the links. It is good to know that I'm not the only one to freqak out over these things :<)

---

### Post by datamason on 2014-09-30
I also have this problem (and was on the way to freaking out, because firefox easily acts unstable, so I tend to follow up on any warning messages when I can). It appears for me when I use the command line with :firefox -P in order to call up the profile manager for the first time. Otherwise I use the launcher.  That said, this did not happen under Linux Mint 16 (I just upgraded to 17).

---

