---
title: "[SOLVED] Problems with jpeg dates"
date: 2007-09-11
forum: General Help
---

### Post by eapache on 2007-09-11
My digital camera's firmware screwed up somehow (Kodac c763), and all of the photos that were on it at the time got corrupted metadata (at least, that is my conclusion). All the photos themselves are fine (and viewable), but I'm having the following problems:

1) Under the 'Image' tab in the file properties in nautilus it says "failed to load image information".

2) When imported into f-spot, each photo gives an error, although they do show up after restarting f-spot. They then show up under the year 2034 (my camera's date was set correctly).

3) When I use the 'adjust date' function in f-spot, it acts erratically, jumping around to apparently random dates (all >=2034).

4) Despite the fact that the f-spot feature to  write metadata changes to file is enabled, when the photo dates are changed and reloaded into the f-spot database, they reappear under 2034.

My conclusion is simply that the metadata is corrupt. Is there a way to simply strip the metadata out? (I've seen several different posts on adding & manipulating metadata, so once the corrupted bits are gone, I should be fine.) I have a copy of XP available if there is a better tool for it, but I'd prefer not to :)

PS I know my way around the command line, so if you can provide a command for metadata manipulation, I can script a batch job myself.

---

### Post by mrxinu on 2007-09-11
You should be able to blow out all the EXIF data with exiv2.

---

### Post by eapache on 2007-09-12
Thanks, I'll install it and take a look.

---

