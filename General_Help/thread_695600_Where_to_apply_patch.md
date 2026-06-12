---
title: "Where to apply patch"
date: 2008-02-13
forum: General Help
---

### Post by Ubundood on 2008-02-13
Hi there. Newbie here trying to apply a patch.

Have tried with 'patch -p0 < patch-file-name-here' from the top directory and also from /usr/src but the files it should affect are never found.

I got the patch from [here]("http://lists.alioth.debian.org/pipermail/pkg-gnome-maintainers/2006-August/025717.html") and it is supposed to apply some changes to metacity. [This is the actual patch file]("http://bugzilla.gnome.org/attachment.cgi?id=67516&action=view").

It should affect the files 'src/display.c', 'src/prefs.c' and 'src/prefs.h', but they are nowhere in my system.

I was thinking maybe it's not a patch to be applied on an installed version of Ubuntu, that maybe it's just for metacity developers.

Any help is very much appreciated. 

By the way i'm using Gutsy, Thanx!

EDIT: or maybe this patch is to be applied on Debian, not on Ubuntu.

---

### Post by trippinnik on 2008-02-13
well first you have to download the Metacity source.  
```
sudo apt-get build-deps metacity-common
```
```
sudo apt-get source metacity-common
```
should do the trick. then apply the patch to the correct files, you may need to find out where each of them is
and finall you'll need to build metacity,
```
./config
```
```
make
```
```
sudo make install
```
restart your X server and you should have your custom built metacity

---

### Post by Ubundood on 2008-02-14
Thanks for the help. I followed your steps, applied the patch to the source files but 2 hunks failed. Do you think it's safe to go ahead with the process?

I suppose this is due to the fact that the patch was intended to be applied on Metacity 2.14.5-1 and i downloaded 2.20.0. What's the code to download that specific version?

Many thanks in advance.

patching file display.c
Hunk #1 succeeded at 66 (offset 2 lines).
Hunk #2 FAILED at 1779.
1 out of 2 hunks FAILED -- saving rejects to file display.c.rej
patching file prefs.c
Hunk #1 succeeded at 60 (offset 4 lines).
Hunk #2 succeeded at 105 (offset 5 lines).
Hunk #3 succeeded at 155 (offset -8 lines).
Hunk #4 FAILED at 413.
Hunk #5 succeeded at 1023 (offset 28 lines).
Hunk #6 succeeded at 1781 (offset 89 lines).
Hunk #7 succeeded at 1875 (offset 95 lines).
Hunk #8 succeeded at 3000 (offset 123 lines).
1 out of 8 hunks FAILED -- saving rejects to file prefs.c.rej
patching file prefs.h
Hunk #1 succeeded at 56 (offset 4 lines).
Hunk #2 succeeded at 87 (offset 4 lines).

---

### Post by trippinnik on 2008-02-15
I don't know what would happen. But since it failed somethings off.  Maybe you can try the Metacity irc channel or something.  I've installed lots of stuff from source, but I don't usually need to apply patches to anything. Sorry I can't be of more help than that.

---

