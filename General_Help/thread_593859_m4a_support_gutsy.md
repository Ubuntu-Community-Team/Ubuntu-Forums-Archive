---
title: "m4a support gutsy"
date: 2007-10-27
forum: General Help
---

### Post by cessna_89702 on 2007-10-27
How do I get m4a support in Ubuntu 7.10??
Trying to play music with banshee

---

### Post by p_quarles on 2007-10-27
Some more details would be helpful (like what you've tried so far, where you got the files, etc.).

Anyway, if you purchased these files on iTunes, they are DRM'd, which means that the only way to get them into a Linux-readable format is to use iTunes itself to burn them to a CD. iTunes 7.xx works with the latest version of Wine, if you don't have access to a Windows box. 

If they're not DRM'd, then the gstreamer plugins should take care of this.

---

### Post by spikeb on 2007-10-27
> **cessna_89702 said:**
> How do I get m4a support in Ubuntu 7.10??
Trying to play music with banshee

install gstreamer-plugins-bad (if you do a search for aac in add/remove it will show up)

---

### Post by lucksin on 2007-10-30
Hi i installed gstreamer-plugins-bad but still i cant play m4a files in rhythmbox. :(

---

### Post by bcrom on 2007-11-09
bump

---

### Post by dekaru on 2007-12-07
my problem is similar on rhythmbox and gutsy.. i can play m4a files but the processor usage peeks and the song skips, so hearing it it's not really an option... any suggestions ?

---

### Post by iris-n on 2007-12-16
I have some similar problem; m4a playback works fine on totem (under xine), but when I try to import the files to rhythmbox it doesn't, and when I try to play them it gives me a "Problem occurred without error being set. This is a bug in Rhythmbox or GStreamer."
I already have the good, the bad and the ugly plugins.
Which one did you use to play them in rhythmbox, **dekaru**?

---

