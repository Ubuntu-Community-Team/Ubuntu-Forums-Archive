---
title: "No Sound!!"
date: 2007-03-21
forum: General Help
---

### Post by mrfelker on 2007-03-21
Help!  I am using Edgy Elf (6.10) and all of sudden (with no changes) the sound stopped working.  Is is still working under Windows, Fedora and openSuse, - which I also have installed.  Any ideas??:confused: 
e

---

### Post by buuntuu! on 2007-03-21
hi there!
what do you mean by "all of a sudden"? did you do any updates?
i had this issue after a kernel-update, and it turned out to be just  my pcm-channel being muted for some reason.
in gnome, control your speaker icon (click, then Cntrl+O) you'll see if pcm is muted.
otherwise open alsamixer from the terminal and see if any channels are muted.
hope it helps...

---

### Post by drpaul on 2007-03-21
Yes, the first thing to check are the settings in alsamixer. If they're fine, then I would suggest you reinstall the alsa driver. My sound was quitting from one application to the next over the past week, and it fixed it [mostly] for me.

Paul

---

### Post by mac.ryan on 2007-03-21
I don't know if what following will help you, but...

...at times, I got the same problem when plugging/unplugging the headset into the sound card. I discovered that some of the channels in alsamixer were automatically muted everytime I was inserting/removing the jack. Un-muting them would recover the sound (albeit a couple of times I had to restart the system after having unmuted).

I don't know what it causes that, but I read on other threads that people who compiled themselves the latest alsamixer got many problems fixed.

Make sure all the channels are displayed (i.e. not hidden) in the alsamixer.

Best luck!

---

