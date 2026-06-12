---
title: "Firefox 3 image problems"
date: 2008-01-27
forum: General Help
---

### Post by computerwolf on 2008-01-27
I have just finished a fresh install of gutsy on my computer and the first thing I did was to download firefox 3.0b2. When I load it, everything seemed like it was running fine until i visited a few pages. It seems that randomly, a picture will not display and it will just be blank. This has happened on pages such as google and youtube, and the pictures are just .png and .gif files. I can right click on them and view the image, and all I get is a blank image. I know the images are fine because on all of my other computers with firefox 3.0b2, the images are fine, so that means it is a problem with my current install. The images are also fine if I download them from the browser. How do I find out what is causing this?

The attached screenshot is of [http://www.google.com/firefox?client=firefox-a&rls=org.mozilla:en-US:official](http://www.google.com/firefox?client=firefox-a&rls=org.mozilla:en-US:official) and the image that is not displaying is [http://www.google.com/images/firefox/sprite.png](http://www.google.com/images/firefox/sprite.png)

---

### Post by sports fan Matt on 2008-01-27
Funny, that works here..have you tried (just checking to see) Swiftfox [http://www.getswiftfox.com/](http://www.getswiftfox.com/) It has sped up my computer

---

### Post by computerwolf on 2008-01-27
Well, I just installed swiftfox on your suggestion and loaded it up. Same problem with the same images. Just for another example, the logo for youtube on youtube.com is another one that is blank.

---

### Post by computerwolf on 2008-01-27
Another update on the issue, I have another computer on the same network with Gutsy on it and I put firefox 3.0b2 on it and everything is fine. Also, if I downgrade to firefox 2, it shows up perfect as well. So this means it has something to do with this specific installation of gutsy and firefox 3. I have checked all the security settings as well and nothing is trying to block any images or anything from any of the websites. Pinpointing the exact type of image that is not being shown is also turning out to be a difficult task.

---

### Post by banewman on 2008-04-06
I'm having the same issue - any solution yet?

---

### Post by matts@yoyo.org on 2008-04-07
Same problem here, and it's affecting me with 3.0b3 and 3.0b4 (both on Hardy).

My machine at work with the same version doesn't have this problem - very weird indeed.

---

### Post by matts@yoyo.org on 2008-04-07
As per the following bug report: [https://bugzilla.mozilla.org/show_bug.cgi?id=411831](https://bugzilla.mozilla.org/show_bug.cgi?id=411831)

Adding

```
Option "XAANoOffscreenPixmaps" "true"
```

to the video driver section of /etc/X11/xorg.conf has fixed this for me.  I hope it works for you too!

---

