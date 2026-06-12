---
title: "Trouble with gtk applications in 13.10, hang when open a dialog."
date: 2013-10-22
forum: General Help
---

### Post by cblhxx on 2013-10-22
I found in my 13.10 ubuntu, applications 'gtkpod' and 'deluge' hang whenever I open a dialog and press OK button to save something.
At first, I though it's an instability issue. Then I installed them on another 13.04, both of them worked well.
All other applications in my 13.10 work fine as well, so the only thing common in both applications is they are using gtk.

Did anyone experience the same problem?

---

### Post by centrinoy on 2013-10-29
I have the same issue with deluge-gtk I have no idea why.
sometimes it freezes when I add a magnet link, I was wondering if that has anything to do with libttorent and proxy settings
or something else

PS: all worked super fine before upgrading to 13.10

---

### Post by gtxseries on 2013-11-11
**Hello there,**

I'd like to join in this problem:
I use ***Ubuntu 13.10 amd64*** and I experience this a lot, since my music player of choice is deadbeef, which happens to be GTK2/3. Whenever I save a playlist, or open the preferences window and press OK, it hangs. Nevertheless music still plays flawlessly, but I have to right click on it on the dock and press quit several times before I can force quit it and relaunch. It's especially annoying, since I modify my playlists a lot nowadays. It happens either with GTK2 or GTK3 modes in Deadbeef. And probably with other GTK apps too.

I use a custom compiled 3.11.6 kernel. The source was downloaded from the ubi repos and the only custom option is that I compiled it for AMD processors, since I have a Phenom II X4 955. Everything else is default. But it happens with the generic kernel too.

**Edit:** The system is up to date by the way, should it matter...

---

