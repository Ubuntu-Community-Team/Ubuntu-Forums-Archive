---
title: "Hulu videos won't play anymore"
date: 2015-09-27
forum: General Help
---

### Post by pretty_whistle on 2015-09-27
Hulu videos were playing fine for a long time but it now gives an error.  This occurs regardless of which browser is used.  According to Hulu they've found a Linux bug on their end.

What I'm wondering is if there's anything I can do on my end to fix it?  Does anyone know of anything??

I have Ubuntu 14.04 LTS.

---

### Post by deadflowr on 2015-09-27
Are you running with hal?
[http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045](http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045)

---

### Post by pretty_whistle on 2015-09-27
Thanks, I'll try that.
:)

---

### Post by pretty_whistle on 2015-09-28
It failed.  :(

Oh well.

---

### Post by deadflowr on 2015-09-28
Have you stop and restarted any instances of Firefox that might have been running?
I'd also recommend clearing out any all plugin settings and cache data within Firefox.

Also, you may need to clear out the .macromedia folder.
(Though I never had to do this)


Note that Chrome/ chromium are dead ends in that they cannot use the hal method.

---

### Post by pretty_whistle on 2015-09-28
> **deadflowr said:**
> Have you stop and restarted any instances of Firefox that might have been running?
I'd also recommend clearing out any all plugin settings and cache data within Firefox.

Also, you may need to clear out the .macromedia folder.
(Though I never had to do this)


Note that Chrome/ chromium are dead ends in that they cannot use the hal method.
Where is the .macromedia folder?

---

### Post by ajgreeny on 2015-09-28
> **pretty_whistle said:**
> Where is the .macromedia folder?
It's a hidden folder in your home.  Open up the file manager and hit Ctrl+H to show all hidden files and folders (all names start with a .)

---

### Post by pretty_whistle on 2015-09-28
> **ajgreeny said:**
> It's a hidden folder in your home.  Open up the file manager and hit Ctrl+H to show all hidden files and folders (all names start with a .)
Ok.

I checked and it's empty.

---

