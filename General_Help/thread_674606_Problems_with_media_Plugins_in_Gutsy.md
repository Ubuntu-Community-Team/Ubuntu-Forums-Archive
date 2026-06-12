---
title: "Problems with media Plugins in Gutsy"
date: 2008-01-21
forum: General Help
---

### Post by jesushero on 2008-01-21
So I've finally narrowed down my random crashes to media plugins!! 

These are the Flash and Java Runtime Environment for Firefox, mp3 and other audio codecs and all non-default compressed video codecs. Every time I use any of those in any way, the system crashes. It may not happen immediately, but it will happen! 

I've been running my computer for a few days now, only running open office since boot. It had been running problem free for 3-4 days!!! As soon as I started firefox and accessed a flash website, a few minutes later it crashed!! Same thing again some days later with a few mp3 files. 

So this means, the system only crashes if I use any kind of non-default media codecs since boot. If not, it can run for days...

What can I do to be able to use the plugins with no crashes???

---

### Post by Metaljaz on 2008-01-22
Here is a wiki that you may find helpful. Scroll through the list and find the plug ins that you have installed and try to install them as instructed on the wiki. You may be missing some codecs or a version conflict. Even though this is the gusty wiki I went back to the feisty wiki for some things that i installed. Good Luck.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by jesushero on 2008-01-22
Thanks, that was quite informative. I do have a problem though, I installed flash directly from the adobe (or something related) website, without using synaptic or apt-get.. How do I uninstall it??? Is gnash more stable? I was thinking of removing flash nonfree and getting gnash instead. 

The flash I currently have does not appear on the add/remove or on synaptic..

---

### Post by Metaljaz on 2008-01-23
Read through this thread...at the bottom:

[http://ubuntuforums.org/showthread.php?t=464825](http://ubuntuforums.org/showthread.php?t=464825)

Is gnash more stable?
Just been reading that it was buggy. Not totally sure, never used it.

---

### Post by wolfen69 on 2008-01-23
here's the flash fix for firefox:

if you installed flash-plugin or gnash, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by jesushero on 2008-01-24
How do I manually remove flash when it is not on Add/Remove or Synaptic????

Where do I find it?

PS: It was installed in root, not my home directory.. I didn't use make install to install it so make uninstall as suggested  would not find anything to uninstall!

---

### Post by Metaljaz on 2008-01-24
Try this command. 

sudo apt-get remove --purge flashplugin-nonfree

If that does not work try this:
From the address bar type:
about:plugins
Look for the flash player that is installed. Should see something like this:
Shockwave Flash
    File name: libflashplayer.so
    Shockwave Flash 9.0 r48
Now you need to locate libflashplayer.so. Check your root and home directories.
Be sure to got to view>show hidden files.

---

### Post by jesushero on 2008-01-25
> **Metaljaz said:**
> Try this command. 

sudo apt-get remove --purge flashplugin-nonfree

If that does not work try this:
From the address bar type:
about:plugins
Look for the flash player that is installed. Should see something like this:
Shockwave Flash
    File name: libflashplayer.so
    Shockwave Flash 9.0 r48
Now you need to locate libflashplayer.so. Check your root and home directories.
Be sure to got to view>show hidden files.

I did that, and removed the libflashplayer.so 

I checked the installer source code and I think it basically only copies libflashplayer.so to the firefox plugins directory. Firefox is way more stable now! It did crash a couple of times with no flash plugin installed though... Should I remove more plugins? Or is it just firefox now? Should I go for gnash or the nonfree fix? Which is the most stable??

---

### Post by Metaljaz on 2008-01-25
Ok you have one more file to remove. Here are the complete instructions:

    Manual removal (for users who installed the plug-in via Install script):

    Delete libflashplayer.so binary and flashplayer.xpt file in directory /home//.mozilla/plugins/ 

And for those with RPM package systems:
    RPM removal:
    As root, enter in terminal: # rpm -e flash-plugin Click Enter and follow prompts

I have had much success with flash and know nothing about gnash. If you wish to reinstall flash 9 try this link:

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

