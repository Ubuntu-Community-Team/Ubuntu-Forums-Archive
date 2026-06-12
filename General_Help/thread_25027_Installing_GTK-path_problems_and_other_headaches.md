---
title: "Installing GTK-path problems and other headaches"
date: 2005-04-09
forum: General Help
---

### Post by CelticWhisper on 2005-04-09
Hey all, first post on this forum, I wish I could say I'm here under more pleasant circumstances.

I've been using Ubuntu for a little while, only a few days, and it seems like a good jack-of-all-trades distro.  However, I'm having some trouble updating Firefox to 1.0.2.  Says it wants a newer version of GTK.  Okay, whatever, let's do that.

I downloaded the latest versions of

GTK+
atk
glib
pango

and proceeded to compile glib.  Trying to compile atk, though, returns an error about not finding glib, saying I should update my PKG_CONFIG_PATH environment variable.  The exact text is as follows:

> pkg-config --modversion glib-2.0 returned 2.6.4, but GLIB (2.4.7) was found!  If pkg-config was correct, then it is best to remove the old version of GLib.  You may also be able to fix the error by modifying your LD_LIBRARY_PATH environment variable, or by editing /etc/ld.so.conf.  Make sure you have run ldconfig if that is required on your system.
If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH to point to the correct configuration files
no
configure: error:
GLIB 2.5.7 or better is required.  The latest version of GLIB is always available from [ftp://ftp.gtk.org](ftp://ftp.gtk.org).  If GLIB is installed but not in the same location as pkg-config add the location of the file glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

So, the questions this raises are:
-Is pkg-config right or wrong?
-EXACTLY how do I go about modifying LD_LIBRARY_PATH and EXACTLY how do I go about modifying PKG_CONFIG_PATH?
-Does my system require ldconfig to be run?
-I unpacked glib 2.6.4 to my /home, under ~/glib-2.6.4  How would I add that to any necessary variable, and which variables need it added?
-How do I go about searching my system for the necessary files?  I've tried ls -grep at the root directory, I've tried "find" "search" "sniff" and every other term I can think of for searching for something, and the only lead I got was that there's something called "locate" but it isn't installed.

Now, if I were just concerned about getting my latest Firefox, I'd use the binary installer the Moz guys have so kindly put together.  Thing is, I'm doing this in an effort to learn how to properly compile and install software from source under Linux.  Sooooo...long way it is.

*sigh*  I'm determined to make this work, as I NEED to get smart about how to do this stuff, but...what a ride.

Anyway, I have to warn you that I'm going to be a million questions a minute the whole way.  My knowledge of Linux is very piecemeal at this point, so I'm going to need someone who can stick this out with me for the long haul and who won't strangle me for asking every noobish question under the sun.

Thanks in advance for the help.  I am forever in your debt.

---

