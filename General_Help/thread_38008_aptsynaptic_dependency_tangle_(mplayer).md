---
title: "apt/synaptic dependency tangle (mplayer)"
date: 2005-05-29
forum: General Help
---

### Post by LazyBoy on 2005-05-29
I'm trying to install mplayer, but get the following.

$ sudo apt-get install mplayer-586
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-586: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages

I already commented out the cdrom reference in /etc/apt/sources.list as another thread suggested.  
Any other ideas?

Don't bother to suggest a different video player.  I need to install mplayer.

LB

---

### Post by Leif on 2005-05-29
I may be wrong, but I don't think mplayer-586 works, go for 386 instead. If you have marillat repos, go and force the hoary version in synaptic, it should install after that.

---

### Post by arnieboy on 2005-05-29
this issue has been discussed quite a few times and the whole guide to installing mplayer is already there on this forum. 
Please visit [http://www.ubuntuforums.org/showthread.php?t=31061](http://www.ubuntuforums.org/showthread.php?t=31061)
I have discussed in detail how to compile and install mplayer from source. You can also install mplayer with apt (the method for which is detailed in the very next post on the same page).
Hope this helps.

---

