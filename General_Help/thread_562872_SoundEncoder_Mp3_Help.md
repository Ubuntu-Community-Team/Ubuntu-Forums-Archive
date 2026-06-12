---
title: "SoundEncoder Mp3 Help"
date: 2007-09-29
forum: General Help
---

### Post by Green_biri on 2007-09-29
Hi everyone. I'm having some problems with the SoundEncoder using the Mp3 encoding... I've already installed the **gstreamer0.8-lame** package, but it still says that I don't have it...

Some help would be apreciated :rolleyes: 

P.S.: I've been using Windows for 12 years, and I changed to Linux last week... It's worthless to say that It's ultra-fast, ultra-easy to use and what-so-ever :razz: 
Thanks to all Ubuntu comunity!

---

### Post by tgalati4 on 2007-09-29
I'm using gstreamer0.10-lame.  Check for preferences in SoundEncoder.  Perhaps there is a file pointer that needs to be explicitly told where lame is located.  Something like:

/usr/lib/gstreamer-0.10/libgstlame.so
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0

This is required in Audacity.  I'm not sure about SoundEncoder.

---

### Post by bubbalouie on 2007-09-29
Is it possible you have a broken dependancy, I may be wrong but you should also need LAME itself, have you checked in adept (or synaptic) that lame is in fact installed too. I had the problem with a CODEC once before.

An easy way to test would be to just enter the following into a console:

** sudo apt-get install lame**

If you already have LAME it will say so, otherwise it will install.

---

### Post by Green_biri on 2007-09-30
Yeah, LAME was uninstalled... Thanks for the help! :D

---

### Post by bubbalouie on 2007-10-02
No worries, glad to be of assistance :)

---

