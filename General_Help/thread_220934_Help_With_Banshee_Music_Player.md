---
title: "Help With Banshee Music Player"
date: 2006-07-22
forum: General Help
---

### Post by swooshvapors13 on 2006-07-22
I downloaded the Banshee music client today and I mounted my iPod and imported songs to Banshee from it. When I tried to play the file, it told me that I didn't have the right decoder installed to handle that kind of file. Can someone please tell me where I can find such a decoder? Thanks!

---

### Post by swooshvapors13 on 2006-07-22
I believe the format of the music is M4A...

---

### Post by jordilin on 2006-07-22
If you bought the songs from itunes, I'm afraid you'll not be able to play them with Linux. They use the aac format if I'm not wrong, but let's await if someone has tried to play aac files in Linux

---

### Post by PriceChild on 2006-07-22
Files from itunes are DRM protected are they not? Meaning that you are forced to play them on ipods and itunes.

Sorry.

---

### Post by swooshvapors13 on 2006-07-22
They may be however I just wanted to play songs that are on my iPod that I put on it from a CD. It won't let me play any songs that came from my iPod no matter where I got them from.

---

### Post by PriceChild on 2006-07-22
Have you installed the restricted formats?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by AirRaven on 2006-07-22
Try using Automatix to install the "w32codecs" package. I think it's listed as "Media Codecs".

---

### Post by aysiu on 2006-07-22
Are you sure it's w32codecs you need? I thought it was gstreamer0.10-plugins-ugly.

---

### Post by Jagot on 2006-07-23
To play .m4a (AAC) files you need gstreamer0.10-plugins-bad-multiverse

---

