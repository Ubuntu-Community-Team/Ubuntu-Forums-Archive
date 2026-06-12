---
title: "banshee &amp; replay gain"
date: 2013-03-08
forum: General Help
---

### Post by LifeEnemy on 2013-03-08
Hi all,

I'm trying to figure out how to make Banshee work with replay gain. I have a few albums where the "intro" track is louder than the rest, and the volume always drops when switching to the second track. It's not a big deal, but it's hurts the immersion. From what I've read, Banshee is supposed to support replaygain. How can I make it use it?

The one that convinced me to post is an mp3 (as most of my files are) if that matters.

Thanks!
Paul

---

### Post by vanadium on 2013-03-08
That you experience the drop in volume indicates that banshee is effectively applying replay gain. However, it is applying track replay gain, not album replay gain. You should look for an option in Banshee that tells it to use the album replay gain. Unfortunately, I do not have Banshee installed myself, so I cannot be more specific.

Of course, there is also the chance that replaygain was wrongly applied to your files. For mp3, there is also replaygain where the audio data themselves are (losslessly) changed. The advantage of that approach is that the adjustment will work on any mp3 player, not just the ones that support replay gain tags. If your files would have been processed with such replay gain *and* track based, then you would also have this issue. In that case, the resolution would be to undo the replay gain (mp3gain stores undo tags for that purpose) and repeat it properly. In the unlikely case that the mp3gain undo tag would be lost, it will be difficult to resotre the correct relative volumes of the files.

---

