---
title: "[SOLVED] can't see thumbnails in nautilus"
date: 2007-08-26
forum: General Help
---

### Post by wrathkeg on 2007-08-26
Hi.  I have a load of JPEGs on my system.  In Nautilus, I can see thumbnails for all of them (I am the owner of them, if that matters).  However, another user on the system can only see thumbnails of some of them.  Any ideas how to fix it?  I don't think it can be a problem with permissions.  For example, the user can see the thumbnail of this image:
```
-rwxrwxr-x 1 wrathkeg users  81939 2007-06-23 17:34 lo-20070623-101820.jpg
```
but not this one, which is in the same directory:
```
-rwxrwxr-x 1 wrathkeg users 713687 2007-06-23 14:35 20070623-143526.jpg
```
I also don't think that it can be down to file size: I have checked the Nautilus preferences, and they are set to show thumbnails 'always', and for files smaller than 5MB.

Any suggestions appreciated.

WK

---

### Post by kaylus on 2007-08-26
What is showing up for the thumbnails, i.e. where they are supposed to be is any kind of image showing up? I would start out by checking your .thumbnails directory it's underneath your home directory so: /home/wrathkeg/.thumbnails

And make sure the thumbnails were created properly. You can always delete thumbnails from there and let them recreate. Thats the extent of my knowledge on thumbnails but it might just work!

---

### Post by wrathkeg on 2007-08-26
> **kaylus said:**
> What is showing up for the thumbnails, i.e. where they are supposed to be is any kind of image showing up?
Not really. Just what I'd call a placeholder:  the same picture of a seascape for each image.
> 
And make sure the thumbnails were created properly. You can always delete thumbnails from there and let them recreate. Thats the extent of my knowledge on thumbnails but it might just work!
And it did.  I just deleted all of the thumbnails, both from my own ~/.thumbnails , and from that of the user in question.  Seems to be fixed now.  Thanks.

WK

---

