---
title: "Firefox and epiphany randomly close on certain sites (now in HI-DEF)(applause)(clap)"
date: 2007-12-24
forum: General Help
---

### Post by JimmyHopkins on 2007-12-24
Sorry for the likeness- to other threads, but no one seems to be able to solve this problem.
This is a video of firefox and epiphany closing websites. Epiphany closes after anything but google. Firefox can at least open wikipedia. My system is a P4 3 GHZ, with 128 MB video ram (a geforce FX 5200_ with 512 MB of RAM.

I've even completely reinstalled gutsy this morning. However, .mozilla and my /home reside on a different partition than the rest of ubuntu does, so maybe firefox didn't get completely deleted? Other internet apps work, such as frostwire, IRC, email, ex cetera.

Now to answer how I'm posting this message. I'm running XP on the same machine. I ran into this problem when, in ubuntu, I tried to install a rhapsody plug-in for firefox that was required for some free internet radio station, while reading the consumerist. I unstalled the rhapsody plug in. I'm running the latest version of firefox that the default gutsy depositories will let me (i.e. not firefox 3 beta). I have ad block plus, chatzilla, pennypacker, pdf download, and flash (adobe flash, not the new opensource one) installed in firefox. Epiphany is a default installed, with no bookmarks, plugins, nothing.

EDIT: I should mention that the live cd of gutsy worked fine.

Link to video: [http://www.megaupload.com/?d=VRM0FY0J](http://www.megaupload.com/?d=VRM0FY0J)

Thanks in advance!

---

### Post by ~LoKe on 2007-12-24
Try creating a new profile.  You could always delete ~/.mozilla and then reconfigure firefox (I think this would work):
> sudo dpkg-reconfigure firefox

---

### Post by daengbo on 2007-12-24
I'll guess that you've got some badly-acting extensions or cache in your profile. Back up your bookmarks, delete .mozilla, remove any extra Firefox extensions, and try again.

---

