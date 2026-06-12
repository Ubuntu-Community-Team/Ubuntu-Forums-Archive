---
title: "Chromium not displaying any pages, even Settings"
date: 2014-02-07
forum: General Help
---

### Post by evilbrent on 2014-02-07
So I was looking for a way to fix a problem of youtube videos (almost) constantly saying "video currently not available" (but only almost constantly, which is the annoying thing). I found advice to upgrade codecs, which seems relatively harmless:

```
sudo apt-get remove chromium-codecs-ffmpeg
sudo apt-get install chromium-codecs-ffmpeg-extra
```

But then webpages were coming up blank. Even chrome://settings was blank. Nothing. Totally blank.

So I thought "Oh, hey, maybe I should have closed chromium before upgrading it, so I closed it and replaced it with a new fresh version:

```
sudo apt-get remove chromium-browser
sudo apt-get install chromium-browser
```

Still blank.

This causes a bit of a problem for me - I can work around youtube videos not loading, but not even being able to see any visuals on any website, including URL's within my own computer, is going to reduce my internet enjoyment capabilities.

Any ideas? Thanks for reading.

---

