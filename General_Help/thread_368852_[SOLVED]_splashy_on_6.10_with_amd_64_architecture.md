---
title: "[SOLVED] splashy on 6.10 with amd 64 architecture"
date: 2007-02-23
forum: General Help
---

### Post by unebaguettesvp on 2007-02-23
has anyone installed splashy on ubuntu 6.10 with amd 64 bit architecture? i tried installing the latest version, 1.8.1, by compiling the source code. the instructions i followed were:

[http://splashy.alioth.debian.org/wiki/doku.php?id=installation#release_sources](http://splashy.alioth.debian.org/wiki/doku.php?id=installation#release_sources)

it seemed to work just fine for a minute when it was checking to see if my system had everything. but then it stopped and the error it gave was:

"Consider adjusting the PKG_CONFIG_PATH environment variable"

it said i was missing the directfb library along with another library that i forgot the name of. i'm at work. sorry!

anyway, i checked synaptic package manager and searched for the directfb library and it was under a different name. something like libdirectfbXXXX with XXXX being some number. but i guess i don't know how to set the PKG_CONFIG_PATH environment variable correctly.

you use the export command right? i'm sorry. i'm totally a linux newbie (3 days!). what is the correct syntax? thanks!

is there anything else i need to worry about?! i uninstalled usplash just like i read everywhere.

i tried this too but it didn't work:
[http://ubuntuforums.org/showthread.php?t=41709](http://ubuntuforums.org/showthread.php?t=41709)

thank you so much in advance!

---

### Post by unebaguettesvp on 2007-02-24
i would really appreciate some help! i don't have a boot screen anymore because i have been fooling around with it too much. how would i do this?

checking for splashy... configure: error: Package requirements (glib-2.0, directfb >= 0.9.22) were not met:

No package 'glib-2.0' found
No package 'directfb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables splashy_CFLAGS
and splashy_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

thanks in advance!!!

---

### Post by unebaguettesvp on 2007-02-25
FYI, I fixed this problem!

So, I'm extremely new to linux and didn't realize that when this script was asking for glib-2.0 and the directfb libraries, it was REALLY asking for the dev libraries!!! This was because I was compiling it.

So, I saw that I had libdirectfb in Synaptic Package Manager. But what I didn't have installed was libdirectfb-dev!!!

I hope that helps someone else out!!!

---

