---
title: "Not sure what I'm missing, but I can't view some webpage content"
date: 2008-01-23
forum: General Help
---

### Post by CheshireMac on 2008-01-23
Hey folks. I'm up and running on a fresh install of Gutsy, and I've never been happier . . .minus one little bug I noticed today.
I went to view a page ([http://www.cwtv.com/shows/smallville](http://www.cwtv.com/shows/smallville)) and I can load the page, but most of the content is missing, except for the basic stuff (html) . . . I thought I had all my plugins ready, but clearly I'm missing something. This is the only page I can recall having an issue with since this install, so I'm not too worried, but I'd like to know what that page requires for viewing because I'm sure it's not the only site online with that content. 
Any thoughts?

---

### Post by t20racerman on 2008-01-23
They seem to be all Flash based graphics. You must be missing the Flash plugin. Should be in the repositories...

---

### Post by CheshireMac on 2008-01-23
Well, I looked around in the repos, and installed a missing lib file for mozilla, but it did nothing for the issue. I'll keep working on it.

---

### Post by t20racerman on 2008-01-23
The Flash plugin in Firefox is libflashplayer.so 

To see what plugins you have in Firefox, open a new tab and type "about:plugins"  This will tell you exactly what plugins you have installed.

---

### Post by CheshireMac on 2008-01-24
Okay, so I've made no progress to speak of on this issue, but I have discovered the same issue regarding the MySpace music player. Unfortunately, I don't know what I'm missing still.
Does anyone know what that requires?

---

### Post by wolfen69 on 2008-01-24
here's the flash fix for firefox:

if you installed flash-plugin or gnash, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

also, open up synaptic and search for mplayer mozilla. install.

did you install java? search for jre 6.

---

### Post by CheshireMac on 2008-01-24
Well, it worked, but now it's mega slow . . .might be the machine, but I doubt it since it worked in the last install with no issues. 
The player keeps freezing now, and that jams up firefox too. It still responds, but the music is blotchy, and everything creeps.
Anyway to get around that?

---

