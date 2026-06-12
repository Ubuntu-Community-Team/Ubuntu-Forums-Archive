---
title: "Shotwell issues"
date: 2013-06-19
forum: General Help
---

### Post by il_mix on 2013-06-19
Hi everyone.

I've started using Shotwell, and I have a couple of questions for the more hardcore users.

1) all my photos are on a NAS at home. When I made some changes to the photos via Shotwell (rotate the photo, add tag), the modification affect just my database. Is there a way to rotate the photo "phisically" and add the tag to the photo itself? So all users could make modification that everyone else could see.

2) if there's no workaround for (1), and since I've seen that it seems not like a good idea to have a shared database/library (second FAQ [here]("http://redmine.yorba.org/projects/shotwell/wiki/ShotwellFAQ")), is there a good Shotwell alternative that could do these simple tasks?

Thanks to everyone!

---

### Post by eric-yorba on 2013-06-19
> **il_mix said:**
> 1) all my photos are on a NAS at home. When I made some changes to the photos via Shotwell (rotate the photo, add tag), the modification affect just my database. Is there a way to rotate the photo "phisically" and add the tag to the photo itself? So all users could make modification that everyone else could see.

If you enable writing metadata in the Shotwell prefs, it will write tags out to the original files.  More info here:
[http://www.yorba.org/shotwell/help/other-files.html#writing-metadata](http://www.yorba.org/shotwell/help/other-files.html#writing-metadata)

As far as writing out edited versions of photos to disk, Showell will never write modified photos directly to your photo library.  However, you can export modified photos via the File menu.

---

### Post by il_mix on 2013-06-19
Direct response from the developer. Great!
The metadata function seems enough for my purpose. I'll give it a try.
Exporting the modified photos will overwrite the old one? Is there a way to export all the modified photos (and just the modified photos) in a single (sort of) click?
I'm lazy... :)

Thanks!

---

### Post by eric-yorba on 2013-06-19
> **il_mix said:**
> Exporting the modified photos will overwrite the old one?

Nope, it will export wherever you tell it.  Shotwell is non-destructive, i.e. the policy is to never overwrite your original photos.

> Is there a way to export all the modified photos (and just the modified photos) in a single (sort of) click? 

So far there's no way to select all photos that have been modified in Shotwell.  There's a couple of feature requests for this, but no patches have been submitted for either:
[http://redmine.yorba.org/issues/4111](http://redmine.yorba.org/issues/4111)
[http://redmine.yorba.org/issues/889](http://redmine.yorba.org/issues/889)

---

