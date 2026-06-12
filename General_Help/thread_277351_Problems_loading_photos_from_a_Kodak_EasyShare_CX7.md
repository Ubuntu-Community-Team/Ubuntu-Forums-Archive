---
title: "Problems loading photos from a Kodak EasyShare CX7300..."
date: 2006-10-14
forum: General Help
---

### Post by Postman on 2006-10-14
I still am using Ubuntu 5.10 just so it's known.  I was trying to upload photos from my sister-in-law's digital camera which is a Kodak EasyShare CX7300.  The photo uploading application recognizes the camera by brand and type and has icons for the photos.  However, when I click on a photo and select upload, a status bar appears but nothing is filled and nothing is done.  The app is not locked when this happens, it's just nothing is happening as far as uploading is concerned.  Does anyone have any suggestions on how to fix this?  I'm also a newbie in Terminal lingo so please be easy.  Thanks!

---

### Post by Jussi Kukkonen on 2006-10-14
You could try starting the application from the command line, there might be error messages. This should work (when camera is connected):
```
gthumb --import-photos
```

---

### Post by VividHazE on 2007-01-04
I was having trouble figuring out what application to import my videos on my Kodak CX7310 camera but I got it working with gThumb after I installed it, just thought I'd say thanks for this thread ^_^

---

