---
title: "[SOLVED] Make multiple video files be thumbnails in nautilus"
date: 2008-01-08
forum: General Help
---

### Post by djrobthaman on 2008-01-08
I know it's a stupid little OCD thing.  But I have a folder of .avi movie files.  When I view the folder in nautilus some are thumbnails of a screenshot oft he movie itself and some are that film icon.  Does anyone know an easy way to quickly get all of them to be a thumbnail?

Thanks

---

### Post by TeeAhr1 on 2008-01-08
Easily done.  In Nautiuls, go to Edit > Preferences, pick the Preview tab and where it says "Only for files smaller than," jack it up to suit your taste.  Be aware that it'll be a performance killer, especially if you've got a lot of big files in one folder.

regards-
pd

---

### Post by djrobthaman on 2008-01-08
Thanks for the reply but I just tried it and it didn't work.  I had nautilus in the background and I noticed that whenever I changed the setting, the files that already had thumbnails refreshed (there was a bit of a flicker like it went to nothing and then the picture reappeared) but the other files seemed unphased.

I pushed the setting all the way up to 1gb (granted some files are bigger than that but most aren't).

Do you think there may be any other setting I could mess around with?

---

### Post by Anduu on 2008-01-08
I'm pretty sure there isn't anything that can be done....I get the odd video without a thumbnail as well.

I would have to assume it has something to do with the encoding and nautilus just cant extract an image.

---

### Post by djrobthaman on 2008-01-08
You see... the thing is, I know it can be done.  Yes, there are some videos that don't do the thumbnails, but pretty much all of mine had thumbnails before I reinstalled gutsy a few days ago.  Also, I know that if I rename each file, wait about 10 seconds for the thumbnail to load, then rename each back to what I want them to be that each of them will load.  But that's a lot of wasted time for something that has to be able to be automated.

And funnily enough, if I rename the file, and then rename it back to what I want it to be before the thumbnail loads, then the thumbnail won't actually get loaded.

I just really didn't want to have to go to that extreme to get thumbnails.  :(

---

### Post by Anduu on 2008-01-09
Ah...didn't realize they had been working previously...

One thing you can try is deleting your /home/<username>/.thumbnails directory and let nautilus have a fresh go at them.

If that fails I would guess that possibly when you reinstalled Gutsy you forgot to reinstall a codec or some such that you had before which was allowing those videos to be thumbnailed.

---

### Post by djrobthaman on 2008-01-09
Holy crap!!! That did the trick.

Thanks a miillion

---

### Post by Anduu on 2008-01-09
WooT!

---

### Post by CFBauer on 2008-01-12
This worked for me too.  Thanks Anduu!

---

### Post by CFBauer on 2008-01-30
Well it did work for me.  I recently re-installed and moved my videos partition mount point to inside the home directory.  Other previews are showing up, but no videos within my videos folder.  I tried deleting my /.thumbnails folder like last time but had no success.

Does anyone have a suggestion?

edit:
20 minutes later and it's working.  Apologize for the bump everyone.

---

### Post by wingnux on 2008-03-02
That did the trick for me but AVI files won't get any thumbnail =/ I've noticed that when I right-click any avi file and go to it's properties the last tab is "Notes" instead of "Audio/Video" as any other video file (and with a thumbnail!) even tough they play just fine on any player.

Is there any way to make my ubuntu see avi files as video?

---

### Post by Anduu on 2008-03-02
> **wingnux said:**
> That did the trick for me but AVI files won't get any thumbnail =/ I've noticed that when I right-click any avi file and go to it's properties the last tab is "Notes" instead of "Audio/Video" as any other video file (and with a thumbnail!) even tough they play just fine on any player.

Is there any way to make my ubuntu see avi files as video?

Check this thread out it may help you

[http://ubuntuforums.org/showthread.php?t=207730](http://ubuntuforums.org/showthread.php?t=207730)

---

### Post by wingnux on 2008-03-02
Thanks, it helped! :)

---

