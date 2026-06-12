---
title: "Uninterruptible HAL processes, shutdown issues, and playing CDs/DVDs"
date: 2006-08-23
forum: General Help
---

### Post by bookofjude on 2006-08-23
I've been using Ubuntu for about a year, but I'm still somewhat new to everything; I've only recently started using it on my Dell laptop, and have had a few issues, which appear to be connected.

1) I've had trouble shutting it down. More often than not, it reaches "Will now halt" and stops properly, but sometimes it will drop out of the splash screen and hang at "* Will now halt".

2) I've noticed several hanging processes in System monitor, most specifically hald-addon-storage and hald-probe-storage; these seem to occur either at random, or after I attempt to play a CD or DVD, which leads to...

3) Playing CDs in mplayer (via command line) or DVDs in VLC causes both mplayer and VLC to become uninterruptible processes, which is only fixed by shutting down (which leads to problem 1).

I'm not even sure if these issues are connected, though they do appear to be, or how to resolve them. Does anyone have any suggestions or thoughts?

---

### Post by Jiawen on 2006-12-31
I'm having the same problem. A few possibly helpful things: First, see this thread elsewhere on these forums: [http://ubuntuforums.org/showthread.php?t=90379&page=2&highlight=uninterruptible]("http://ubuntuforums.org/showthread.php?t=90379&page=2&highlight=uninterruptible"). Also, there's a possible pointer in the right direction on a Fedora forum: [http://forums.fedoraforum.org/showthread.php?p=673765#post673765]("http://forums.fedoraforum.org/showthread.php?p=673765#post673765").   The suggestion in the latter is to go to > System -> Preferences -> Removable Drives and Storage Media. I de-selected the "Mount removable drives when hot-plugged" and "mount removable media when inserted". It is possible that de-selecting only one of these could fix the problem, but I don't have the energy now to fool around.I'm trying just the first option (having to mount media manually makes me melancholy). We'll see how it works...

---

