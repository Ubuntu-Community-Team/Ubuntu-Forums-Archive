---
title: "Problems with gnome-cd"
date: 2005-11-01
forum: General Help
---

### Post by bison on 2005-11-01
I was getting the unhelpful message 'Drive Error' when I tried to play an audio CD with gnome-cd.  I added the missing symlink (ln -s /dev/hdc /dev/cdrom), and this message is gone, but I still can't play an audio CD.  The drive will recognize the disc and count the tracks, but if I press the play button it immediately reverts to pause.  If I select a different track, it immediately reverts to track 1.

I started it from the command line and got this error message:

bison@bison:~ $ gnome-cd &
[1] 21312
bison@bison:~ $
** (gnome-cd:21312): WARNING **: Could not open resource for writing.

** (gnome-cd:21312): WARNING **: Could not open resource for writing.

** (gnome-cd:21312): WARNING **: Generic IO error

[1]+  Done                    gnome-cd
bison@bison:~ $

Sound Juicer works fine with the same CDs (I tried several).  I installed package 'cdtool', and 'cdplay' works fine.  Any ideas?

---

### Post by BobSongs on 2005-12-26
[QUOTE=bison]I was getting the unhelpful message 'Drive Error' when I tried to play an audio CD with gnome-cd.  I added the missing symlink (ln -s /dev/hdc /dev/cdrom), and this message is gone, but I still can't play an audio CD.  The drive will recognize the disc and count the tracks, but if I press the play button it immediately reverts to pause.  If I select a different track, it immediately reverts to track 1.

I started it from the command line and got this error message:

bison@bison:~ $ gnome-cd &
[1] 21312
bison@bison:~ $
** (gnome-cd:21312): WARNING **: Could not open resource for writing.

** (gnome-cd:21312): WARNING **: Could not open resource for writing.

** (gnome-cd:21312): WARNING **: Generic IO error

[1]+  Done                    gnome-cd
bison@bison:~ $

Sound Juicer works fine with the same CDs (I tried several).  I installed package 'cdtool', and 'cdplay' works fine.  Any ideas?[/QUOTE]
Seems no one answered you on this one. Found this thread drifting in cyberspace.

I've got a friend who has the same problem. Anybody? What might the resource be where the system cannot write?

Anyone?

---

