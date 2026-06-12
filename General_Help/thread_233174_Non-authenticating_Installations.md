---
title: "Non-authenticating Installations"
date: 2006-08-09
forum: General Help
---

### Post by montag451 on 2006-08-09
Recently, none of the installations and upgrades I've been getting through Synaptic have been able to authenticate. This includes ones with the Ubuntu logo beside them. I did a quick search of the forums and didn't find anything pertaining to this. Does anyone know what might cause this problem and if there's anything client-side I can do to fix it? Please let me know if there's any more pertinent information needed for diagnosis.

---

### Post by mlind on 2006-08-10
Could you post the package name and actual error message?

---

### Post by CronoDekar on 2006-08-10
For me, I found that this was because the servers weren't responding.  I changed my entries for the Ubnutu repositories to us.archive.ubuntu.com (a mirror), did an update, and it worked.

---

### Post by Odice on 2006-08-11
Thanks, i had the same problem, i change de cl. to us. in the sources.list and everything is working fine :D

---

### Post by montag451 on 2006-08-12
I'm currently running 6.06. There is no error message, only an node titled NOT AUTHENTICATED when I click Apply if I'm running Synaptic or click Check when running the automatic software update. I've since tried to mark a couple other packages for install at random and they authenticate fine, so it isn't something general like an incorrect repository address. It may be the specific packages, but what weirded me out initially was basic things like the upgraded version of gedit were not authenticating properly, as well as a couple others that don't come to mind. (The version of gedit I have installed is 2.14.4-0ubuntu1, the latest according to Synaptic -- the version that did not authenticate.)

---

### Post by Protagonistics on 2007-07-11
Every time I turn on my computer I am notified that I have updates. I dutifully install them- but I'm now having a recurring problem with some updates which are not installing. what is going on? I click on the Partial Upgrade button

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

compiz
compiz-core
compiz-gnome
compiz-plugins
gaim
libtotem-plparser7
pidgin
pidgin-data
rhythmbox
totem
totem-gstreamer
totem-mozilla


I don't get it.  I'm glad I'm not the ONLY person experiencing this now.

---

