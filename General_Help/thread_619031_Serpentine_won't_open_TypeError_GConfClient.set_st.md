---
title: "Serpentine won't open: TypeError: GConfClient.set_string() argument 2 must be string"
date: 2007-11-21
forum: General Help
---

### Post by acti0nman on 2007-11-21
I'm getting a very strange error.  I have a fresh install of Ubuntu 7.10 Gutsy Gibbon running on a Dell Inspiron 5100 laptop.  The only thing I've installed so far is ubuntu-restricted-extras.  When I click Applications -> Sound and Video -> Serpentine Audio CD Creator, Serpentine does not open.  I try to run it from terminal, and I get the below error.  The only thing I could find that is similar to my issue is from 
[https://bugs.launchpad.net/ubuntu/+source/serpentine/+bug/156216](https://bugs.launchpad.net/ubuntu/+source/serpentine/+bug/156216)
[http://bugzilla.gnome.org/show_bug.cgi?id=481069](http://bugzilla.gnome.org/show_bug.cgi?id=481069)

It seems that a bug report was already filed for this in gnome bugzilla.  However, it seems that only 3 people are experiencing this issue, and one of them didn't even have a real CD-Burner, just a VM.  If this was a real bug, many more people should have been seeing this.  Has anybody had any similar experiences to this and know of a work around or of a way to fix it?  I can't figure this one out at all.  Below is the error I am seeing.  I'm not sure of any other logs you would like me to post, but I will certainly post it for you.
=======================================
Executing Serpentine from terminal
$ serpentine 
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 128, in <module>
    app = SerpentineApplication (locations)
  File "/usr/lib/python2.5/site-packages/serpentine/__init__.py", line 413, in __init__
    Application.__init__(self, locations)
  File "/usr/lib/python2.5/site-packages/serpentine/__init__.py", line 164, in __init__
    self.__preferences = RecordingPreferences(locations)
  File "/usr/lib/python2.5/site-packages/serpentine/preferences.py", line 301, in __init__
    self._on_gconf_device_changed()
  File "/usr/lib/python2.5/site-packages/serpentine/preferences.py", line 455, in _on_gconf_device_changed
    self._device.data = self.__drive_selection.get_device()
  File "/usr/lib/python2.5/site-packages/serpentine/gaw.py", line 153, in <lambda>
    fset = lambda self, value: self.__setter (self.key, value)
TypeError: GConfClient.set_string() argument 2 must be string, not None
=======================================

---

### Post by acti0nman on 2007-11-21
bump.
help? maybe something to point me in the right direction possibly?

---

### Post by Anafiel on 2007-12-07
I'm also getting this error.  Gutsy 7.10 fresh install.  Any Ideas?


anafiel@mudpuppy:~$ serpentine
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 128, in <module>
    app = SerpentineApplication (locations)
  File "/usr/lib/python2.5/site-packages/serpentine/__init__.py", line 413, in __init__
    Application.__init__(self, locations)
  File "/usr/lib/python2.5/site-packages/serpentine/__init__.py", line 164, in __init__
    self.__preferences = RecordingPreferences(locations)
  File "/usr/lib/python2.5/site-packages/serpentine/preferences.py", line 301, in __init__
    self._on_gconf_device_changed()
  File "/usr/lib/python2.5/site-packages/serpentine/preferences.py", line 455, in _on_gconf_device_changed
    self._device.data = self.__drive_selection.get_device()
  File "/usr/lib/python2.5/site-packages/serpentine/gaw.py", line 153, in <lambda>
    fset = lambda self, value: self.__setter (self.key, value)
TypeError: GConfClient.set_string() argument 2 must be string, not None

---

### Post by acti0nman on 2008-02-13
I figured out my problem...it was a stupid oversight...a small one, that an average person should have paid attention to.

Ubuntu is running on this old laptop of mine that I had't opened up in a couple of years.  For the longest time, I thought it had a DVD+CD-RW drive. It didn't. It only had a DVD-ROM drive.  

I read this type of error is usually spewed out if you don't have a CD-RW. So of course serpentine is going to crash when it does its initial start up checks.  

I believe there is already a request to implement a nicer termination method for serpentine related to issues like this.

---

