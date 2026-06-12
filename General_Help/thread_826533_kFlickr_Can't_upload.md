---
title: "kFlickr: Can't upload"
date: 2008-06-12
forum: General Help
---

### Post by mertle on 2008-06-12
Running: Kubuntu Hardy AMD64.

I'm able to run kFlickr, as well as authorize my account to be able to upload with it, but when I go to upload images, the progress window hangs at 0%. I get no errors, it just hangs indefinitely. I then tried downloading Feisty's, Gutsy's, and the new Intrepid's versions of kFlickr in hopes something would work, but instead, I received the following error:

**HTTP request to Flickr.com failed. (msg: Filesize was zero)**

I am, however, able to upload using Flickr's own uploader, version 2.5, under .wine, but it's lacking important features I was used to when I had kFlickr running under Feisty. The newest official uploader doesn't work in .wine at all, for me.

Any ideas?

---

### Post by pixel :-) on 2008-06-26
It worked with me.I don't think the problem is in kFlickr.Apparently it somewhat slow in uploading.Did you give it sore time?Do you have network problems?You are on 56b/s?

run it in a terminal to see if it sais something.

delete /home/YOU/.kde/share/config/kflickrrc maybe an old config file isn't compatible or broken.You will have to reantheticate.

anthenthication with firefox?Try konkeror.

Try a new user with a clean home,and as standard as possible.

Report it [https://bugs.launchpad.net/]("https://bugs.launchpad.net/")

---

