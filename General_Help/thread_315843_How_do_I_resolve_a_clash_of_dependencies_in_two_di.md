---
title: "How do I resolve a clash of dependencies in two different .deb packages"
date: 2006-12-09
forum: General Help
---

### Post by Mangetout on 2006-12-09
I'm trying to set up my Edgy PC for video editing and DVD production; I've installed DVDStyler (because I'm already familiar with it from its Windows version), and installed Cinelerra (from the instructions here: [http://ubuntuforums.org/showthread.php?t=294007](http://ubuntuforums.org/showthread.php?t=294007) ) - well... *tried to* - I can install either program, but not both together - if I install Cinelerra first, DVDstyler won't install and vice versa; they're apparently not in agreement over which version of mjpegtools should be resident.

The advice in the above linked thread on how to install Cinelerra recommends removing any existing version of mjpegtools, but when I do this (in Synaptic), DVDstyler is also removed, because it depends on mjpegtools (so when I try to put DVDStyler back, it won't install because there's already the version that Cinelerra put there and around we go again.

How do I resolve this?  Is this going to involve compiling source?

---

### Post by strabes on 2006-12-10
you could try using "aptitude" instead of "apt-get"

---

### Post by Mangetout on 2006-12-11
Thanks, but I'm not sure how to do that - both of these applications come as downloadable .deb packages - Aptitude (and Synaptic) don't seem to know anything about them.

---

