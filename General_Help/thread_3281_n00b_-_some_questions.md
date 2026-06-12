---
title: "n00b - some questions"
date: 2004-11-04
forum: General Help
---

### Post by kepardue on 2004-11-04
I'm exceptionally new at Linux and am just now picking up the concept of command line, editing config files, and the like.  I love Ubuntu and it seems to have a lot of what I'm looking for in a Linux distribution, but there are a few finer points that escape me.

1 - I have an NVidia GeForce 4 Ti4200 card and two monitors hooked up to it.  I've got the NVidia drivers installed, but I don't know how to set up my second monitor to work.  Any clues?

2 - I realize that everything in the Universe isn't supported, but one of the few reasons that I'm holding out toward Windows is that I'm a huge flight sim aficionado, and I'd like to run the Open Source flight sim FlightGear.  It's listed in Universe, but 1) it's an older version (0.9.4) and 2) after installing it it doesn't seem to appear in Ubuntu's Applications list.  Neither does it appear in  the Run Application menu.

3 - I would like to download a demo version of another flight sim recently converted to Linux, X-Plane, but the download is a bittorrent file.  I've downloaded bittorrent via Synaptic, but unfortunately it doesn't seem to want to open the torrent file downloaded from X-Plane.  I get a "Cannot Display Location" error.  Thoughts?

Many thanks, and all my encouragement for making Ubuntu so great, and for bringing multimedia, the last real step for Ubuntu in Hoary (if and when)!

Best,
Kenneth

---

### Post by tfwo on 2004-11-04
[QUOTE=kepardue]1 - I have an NVidia GeForce 4 Ti4200 card and two monitors hooked up to it.  I've got the NVidia drivers installed, but I don't know how to set up my second monitor to work.  Any clues?[/QUOTE] You have the nvidia's twinview thingie, right? See README both in /usr/share/doc/nvidia-glx or at the nvidia's website on "configuring twinview" [QUOTE=kepardue]3 - I would like to download a demo version of another flight sim recently converted to Linux, X-Plane, but the download is a bittorrent file.  I've downloaded bittorrent via Synaptic, but unfortunately it doesn't seem to want to open the torrent file downloaded from X-Plane.  I get a "Cannot Display Location" error.  Thoughts?[/QUOTE] You should open Terminal, chdir to the directory with .torrent file and run:
$ btdownloadcurses [file.torrent]

There's btdownloadgui, but it will work only if you have wxPython installed. Or you can try other bittorrent clients in universe.

---

