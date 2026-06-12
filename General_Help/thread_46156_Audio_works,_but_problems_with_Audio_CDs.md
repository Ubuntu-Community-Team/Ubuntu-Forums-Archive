---
title: "Audio works, but problems with Audio CDs"
date: 2005-07-03
forum: General Help
---

### Post by mikeb on 2005-07-03
I've installed VLC (the latest stable) and xmms. VLC plays DVDs fine, including the audio. xmms sees the CD and seems to be playing it, but there is no sound. VLC does not see the CD.

Strangely, the CD Players that is included in Ubuntu works perfectly! Suspecting it might be libcdio, I installed that library, but to no avail. Does anyone know what I am missing?

Thanks.

---

### Post by WMCoolmon on 2005-07-03
Maybe XMMS is trying to play analog audio from the CD and the cable isn't hooked up?

---

### Post by varunus on 2005-07-03
This is a problem with XMMS and some sound cards.  To fix it, open XMMS, go to the preferences page for the CD audio input plugin, and check "Digital audio extraction." 

Enjoy.

---

### Post by mikeb on 2005-07-04
Thanks for the suggestions, unfortunately, they don't work. In XMMS, there is an option to check the drive and this is the result when I do: Failed to read "table of contents", maybe no disc in the drive? Failed to check directory. Error: No such file or directory.

In the error log for VLC, it says: no access_demux module matched "cdda"

For the record, this is a regular CD (bought in a store, not homemade). Furthermore, the CDPlayer packed with Ubuntu has absolutely no trouble seeing the disc, the files or playing them.

And, again, VLC is able to play DVDs from the same drive with AC3 passthrough.

Weird, huh? Anyone have any ideas?

---

### Post by mikeb on 2005-07-05
Has no one any idea? Doesn't this sound like a missing library or something else systemic?

---

### Post by pashby on 2005-08-01
[QUOTE=varunus]This is a problem with XMMS and some sound cards.  To fix it, open XMMS, go to the preferences page for the CD audio input plugin, and check "Digital audio extraction." 

Enjoy.[/QUOTE]

Thanks so much for this info - it's been driving me crazy for days - works perfectly now!

Peter

 :)  :)

---

