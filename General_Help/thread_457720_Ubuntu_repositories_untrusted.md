---
title: "Ubuntu repositories untrusted"
date: 2007-05-28
forum: General Help
---

### Post by botulismo on 2007-05-28
I reinstalled Ubuntu 7.04 today due to some problems I thought would just be easier to fix if I started fresh... Those problems are now solved (and probably with less time hunting on the forums and so on) but with a new problem...

Whenever I go to install anything from the regular/default Ubuntu repositories literally EVERYTHING is untrusted... For example, while installing k3b:

> The following NEW packages will be installed:
  k3b kamera kcontrol kdebase-bin kdebase-data kdebase-kio-plugins 
  kdelibs-data kdelibs4c2a kdemultimedia-kio-plugins kdesktop kicker 
  libakode2 libarts1-akode libarts1c2a libavahi-qt3-1 libdbus-qt-1-1c2 
  libflac++5c2 libk3b2 libkcddb1 libkonq4 liblua50 liblualib50 liboggflac3 
  libopenexr2c2a libpcre3 libqt3-mt libsamplerate0 perl-suid pmount 
0 packages upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.4MB of archives. After unpacking 131MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libopenexr2c2a libarts1c2a kdelibs4c2a libk3b2 kcontrol libflac++5c2 
  liboggflac3 kdelibs-data kdebase-data libarts1-akode 
  kdemultimedia-kio-plugins liblualib50 libpcre3 kicker libkcddb1 k3b 
  kdebase-kio-plugins kamera libakode2 libkonq4 perl-suid libavahi-qt3-1 
  kdebase-bin libsamplerate0 libdbus-qt-1-1c2 kdesktop pmount libqt3-mt 
  liblua50 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes


So... how do I reauthenticate the Ubuntu repositories so I don't get this anymore?

---

### Post by Ek0nomik on 2007-05-29
Do you have the update manager running in the background?  Or perhaps Synaptic?

If not, try logging out or restarting and trying again.  If that still doesn't work, reply and I will search on how to fix it along with you.  :)

---

### Post by botulismo on 2007-05-29
No, nothing else is attempting to download whether apt-get, aptitude, synaptic, or the update manager... All give the same responses in some guise or another about (all of) the packages not being authenticated... And rebooting doesn't help, it still gives the same problem. I'm searching right now while trying to multitask with reality (haha).Thanks a lot for being willing to help. This isn't something I've had happen before - well, obviously.

I mean, it doesn't stop Ubuntu from working, or stop me from updating or downloading new packages, however it is annoying.

Shouldn't it just be as clear cut as downloading the keys again?

---

### Post by Ek0nomik on 2007-05-29
You can try:

```
sudo apt-get update
```

Maybe it will fix it?

---

### Post by botulismo on 2007-05-29
You know, this worked, but not after doing the same thing graphically via Software Sources (to see if multiverse  was enabled) and after watching Synaptic claim to be updating the server list...

And, actually, I did this once via command-line aptitude while I was installing beryl from the other repositories. Why would it work with apt-get instead of aptitude? And why would a new Ubuntu installation (from a Ship-It CD no less) be doing it from the get go? Strange.

Thanks for your help!

---

