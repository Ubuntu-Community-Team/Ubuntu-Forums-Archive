---
title: "How do I play a DVD using edgy Kaffeine?"
date: 2006-10-31
forum: General Help
---

### Post by void1 on 2006-10-31
Thanks for the help. I'm a newbie bringing up the new "edgy" version of KUBUNTU.

I'm unable to play a DVD in Kaffeine (newest release). I get the following error message:
The source seems encrypted, and can't be read.
Your DVD is probably crypted. Accoring to your country laws, you
can or can't use libdvdcss to be able to read this disc. (Media stream scrambled/encrypted)

I checked for "libdvdcss" within "Adept Manager", but it is not listed as one of the available packages.

How do I play a DVD?

---

### Post by pay on 2006-10-31
```
sudo apt-get install libdvdcss2 
```
you might need to enable some extra repositories. If you are in the USA it is illegal to use this without paying a fee.

---

### Post by lgambett on 2006-11-26
Hi all,
remember also that the newest DVD readers and/or burners came with the region zone (eg 1=USA, 2=Europe and so on) not set. In this situation dvdcss will not work. To solve the problem install and execute regionset;
sudo apt-get install regionset
regionset
and you are done.
Regards,
Luca:KS

---

### Post by ingo on 2006-12-05
Well, I installed libdvdcss but Kaffeine still resolutely refuses to play any DVDs. Instead it comes up with the following message:

Unable to load Netscape plugin for dvd:/dev/hdd

Am I missing something really silly? VLC can play single VOB files, but not an entire DVD, which is a bit of a pain. 

Hope I'm not stealing the thread, but any ideas welcome.

Cheers

EDIT: Right, manually installed the following packages

> libarts1-mpeglib
libarts1-xine
libakode2-mpeg

and still get the same message.

---

### Post by ingo on 2006-12-06
Right, solved my own prob:

rm /home/ingo/.kde/share/config/kaffeinerc

did the trick. Should that not work for others affected, deinstall kaffeine, remove all traces in your home directory (rm -r /home/ingo/.kde/share/apps/kaffeine/ + the command above) and then reinstall.

---

