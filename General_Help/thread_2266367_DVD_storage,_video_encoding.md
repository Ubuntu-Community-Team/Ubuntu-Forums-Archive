---
title: "DVD storage, video encoding"
date: 2015-02-22
forum: General Help
---

### Post by CaptainMark on 2015-02-22
I've finally joined the the 21st century and have installed a 2TB HDD, rejoice, storage space is no longer an issue for me so I thought I might take this opportunity to de-junk my old DVD collection by throwing away some of my lesser beloved discs and storing the contents on my media server instead.
My question is two fold:
1. Which ripping software to use, preferably one which is easy to use, currently I'm about to try OGMRip from the repos, it seems easy enough so I'm happy to use this unless wiser folks have any good reason for me not to use it.
2. Which video/audio codec to use, I'm a little indecisive over this one so let me give you some of my thoughts on the matter.  I like to use fully open standards where at all possible, I also like to use formats which are likely to be as universally accepted as possible, for example I rip my Music collection to .ogg or .flac format so a video format that has similarities to this would be good. I want the quality to be as good as the DVD is on the disc but don't want the file sizes to be unnecessarily large.

I know this is not much to go on but I'm just looking for advice on codecs, I don't really understand them that much, I was going to choose .ogm format but then noticed you cant encode the video as ogg theora video codec which confused me.

One last question, are different codecs lossy or lossless like audio or is this not an issue with videos?

Thanks for any help/advice

Regards
Mark

---

### Post by Lars Noodén on 2015-02-22
You'd lose some data going from DVD to some other format.  So I would suggest storing the DVDs as ISO 9660 images.  They can still be played that way and no conversion is necessary.

---

### Post by CaptainMark on 2015-02-22
Will I still be able to browse the videos in a library style application, I use banshee locally and Xbmc/Kodi on the server. I presume to rip to iso I can just use dd?

---

### Post by Lars Noodén on 2015-02-22
dd works, so would brasero.  I'm not sure about the other apps you mention, I don't use them.  But VLC seems to have no trouble.

---

