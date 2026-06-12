---
title: "libpostproc6 and libc6"
date: 2005-04-18
forum: General Help
---

### Post by spacemonkey on 2005-04-18
Today I noticed that libpostproc6 is being kept back when I try to apt-get upgrade.  I don't think this is a problem, this is more of a question to satisfy my curiosity and further my knowledge of apt-get.  Synaptic tells me that libpostproc6 depends on libc6, and to upgrade to the new version of libpostproc, I need a different version of libc6 than what is installed.  Is this because libpostproc has been updated in some other repository, most likely the marillat ones, since thats the only non-ubuntu ones I've got, but the version of libc6 is installed from the ubuntu repository, and the ubuntu version of libc6 is not the one that the new libpostproc depends on?

I hope all that makes sense, and like I said, this isn't a problem I don't think, everything works fine, just trying to better my understanding of apt.

---

### Post by tread on 2005-04-18
Sounds like libpostproc6 is the updated package, and the correct libc6 version package isnt available. (libpostproc6 probably came from the non-ubuntu repositories?) 

Since the correct libc6 version is unavailable, libpostproc6 might be held back.

Of course, I'm just guessing here too .. I just moved to ubuntu from an rpm-based distro.

---

### Post by spacemonkey on 2005-04-18
well I didn't install either of them, atleast not directly, they may have been installed as dependencies though.  I did some testing, because like I said, I'm curious.  I removed the marillat repositories, and just as I suspected, libpostproc said that it was at the current version, nothing to update, nothing to hold back, re-add the marillat repositories, and it says it's being held back.

So obviously its updated in the debian reps, and not in the ubuntu reps.  But what I don't understand is why it can't update libc6 from the debian reps, then update libpostproc from the debian reps.  The version of libc6 installed is an ubuntu version, because it contains ubuntu in the version number.  The version it says libpostproc depends on is not an ubuntu version.  Will it not update libc6 to a non ubuntu version?

---

### Post by tread on 2005-04-18
It should be able to do that, if the marillot repositories hold a newer version of libc6. Search for libc6, and then find what versions are available. (I think you have to either right-click the package or go to the menu to do this.) If the marillot version of libc6 is not-verified (unlikely? :-? ) or has some other problem, it might not choose it. 

Anyway, first try and find what versions of libc6 are available to you. I wish I was in linux to try it out too .. but I'm stuck here in windows at the moment.

---

