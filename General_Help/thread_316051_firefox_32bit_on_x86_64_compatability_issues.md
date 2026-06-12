---
title: "firefox 32bit on x86_64 compatability issues"
date: 2006-12-10
forum: General Help
---

### Post by hampycalc on 2006-12-10
Hello everyone, I'm sure someone out there has got a similar setup to me and was wondering how people have circumnavigated it!  Any help would be appreciated.
So, I have the x86_64 installation of edgy (AMD64) on my new 64bit machine which originally came with firefox 2.0.  This was fine until I discovered there was no flash plugin available for the 64bit distros. Nightmare! So, I have installed swiftfox 32bit on my 64bit system with java, flash and realplayer plugins (using Automatix).  My problem is, i still can't get many video feeds running (namely BBC news).  I have tryed sym linking my plugins dir to my firefox plugins dir, but it doen't work, probably because the 32bit version does not work with 64bit firefox plugins.  Have tryed installing the w32codecs, but of course those are not compatible with 64bit systems either!  If there was some was to install a 32bit version of firefox *with* all the neccesary plugins (which would also need to be 32bit compatable) I could create a sym link from my swiftfox plugins to that (or I could just use the 32bit firefox browser).  There may also be another way, I don't know.
Does anyone know how I can sort this out?  Has anyone been in the same situation?  I would be very grateful for any help on the matter.
Tom

---

### Post by Azakus on 2006-12-10
Install mplayer and the 32-bit mplayer-mozilla plugin. The 32bit plugins work with the 64bit player, so all shall work. Here's the code to do it
```
sudo aptitude install mplayer
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb
sudo dpkg -i --force architecture mozilla-mplayer_3.17-1ubuntu1_i386.deb
```

---

### Post by arnieboy on 2006-12-10
> **hampycalc said:**
> Hello everyone, I'm sure someone out there has got a similar setup to me and was wondering how people have circumnavigated it!  Any help would be appreciated.
So, I have the x86_64 installation of edgy (AMD64) on my new 64bit machine which originally came with firefox 2.0.  This was fine until I discovered there was no flash plugin available for the 64bit distros. Nightmare! So, I have installed swiftfox 32bit on my 64bit system with java, flash and realplayer plugins (using Automatix).  My problem is, i still can't get many video feeds running (namely BBC news).  I have tryed sym linking my plugins dir to my firefox plugins dir, but it doen't work, probably because the 32bit version does not work with 64bit firefox plugins.  Have tryed installing the w32codecs, but of course those are not compatible with 64bit systems either!  If there was some was to install a 32bit version of firefox *with* all the neccesary plugins (which would also need to be 32bit compatable) I could create a sym link from my swiftfox plugins to that (or I could just use the 32bit firefox browser).  There may also be another way, I don't know.
Does anyone know how I can sort this out?  Has anyone been in the same situation?  I would be very grateful for any help on the matter.
Tom
try adding **:/opt/realplayer** to the **PATH** variable in **/etc/environment**
```
sudo gedit /etc/environment
```

---

