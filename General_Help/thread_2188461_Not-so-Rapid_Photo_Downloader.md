---
title: "Not-so-Rapid Photo Downloader?"
date: 2013-11-17
forum: General Help
---

### Post by 2CV67 on 2013-11-17
I recently started using Rapid Photo Downloader & am happy with the way it puts photos where I want & doesn't insist on generating its own libraries etc.
I think it is the right application for me here.

But I don't find it rapid.

Once I have checked which photos to download, it seems to take exactly 25 seconds to deal with each photo.
Maybe I need to run some more careful tests, but I have the impression that it's 25 seconds each, whether downloading from the camera (Panasonic Lumix TZ18) or from the SD card reader, and whether the photos are around 2Mo or around 3Mo.
If I download directly, using File Manager, it only takes about one second per photo...

What speed should I expect & what can I do to diagnose/fix this slow downloading?

Thanks for any suggestions!

---

### Post by grier-devon on 2013-11-17
> **2CV67 said:**
> I recently started using Rapid Photo Downloader & am happy with the way it puts photos where I want & doesn't insist on generating its own libraries etc.
I think it is the right application for me here.

But I don't find it rapid.

Once I have checked which photos to download, it seems to take exactly 25 seconds to deal with each photo.
Maybe I need to run some more careful tests, but I have the impression that it's 25 seconds each, whether downloading from the camera (Panasonic Lumix TZ18) or from the SD card reader, and whether the photos are around 2Mo or around 3Mo.
If I download directly, using File Manager, it only takes about one second per photo...

What speed should I expect & what can I do to diagnose/fix this slow downloading?

Thanks for any suggestions!
Sounds like an issue with the software, you would probably have to understand some programming to look at the code and fix it. Why not just use the file manager?

---

### Post by dlynch3 on 2013-11-17
> **2CV67 said:**
> 
What speed should I expect & what can I do to diagnose/fix this slow downloading?



[LIST=1]
[*]I assume you are using the latest version, which is currently 0.4.7. 
[*]Read the special note here: [http://damonlynch.net/rapid/download.html](http://damonlynch.net/rapid/download.html) 
[*]If you have instaleld the latest version, and it's still slow, run from the command line like this, **rapid-photo-downloader --debug**, and report a new bug. 
[*]Also, if you do want to use Rapid Photo Downloader, I strongly recommend downloading directly from a memory card and not a camera. 
[/LIST]

---

### Post by 2CV67 on 2013-11-17
Thanks very much, Damon, for your rapid reaction!

I was using version 0.4.5-3 (installed 16 Oct) in my Ubuntu 13.04 with xfce.

I read your special note, installed the PPA & updated to version 0.4.7.

This now downloads photos perfectly, even from the camera.
I didn't measure, but around one second each.

I find it more convenient to download directly from the camera, rather than extracting the memory card each time, so I would prefer to keep doing that so long as it works OK.
I suppose I can always fall back on the card reader in case of problems and I accept the risk!

Many thanks for your help and for providing this useful application.

---

