---
title: "How to enconding in theora???"
date: 2005-06-24
forum: General Help
---

### Post by Vurdak829 on 2005-06-24
This is a serious problem for me. I've searched google, but i can't find a way to encode from various videos file to theora with ubuntu's application (backports too). Someone can help me to find a way? 
Thx :)

---

### Post by Vurdak829 on 2005-06-25
No one can help me?

---

### Post by GazaM on 2005-06-25
Have you looked into Thoggen? I'm not sure about multiple formats, but you can encode from a dvd just fine. Seriously though, a google search on 'encoding to theora' returns a lot of good results for me, I'd try that again. [http://thoggen.net/](http://thoggen.net/)

---

### Post by Vurdak829 on 2005-06-25
Ok, thx :) i will take a look :)
But the problem is Thoggen is a dvd ripper, i was looking for an encoder also for avi, mpeg, wmv and so files..
I supposed to use mencoder, but on is man pages there aren't no referers or explanation about theora.

Sorry for my english :D

---

### Post by djp on 2005-07-03
If you are using totem-gstreamer, use the following command;

gst-launch-0.8 oggmux name=m ! filesink location=foo.ogg { filesrc location=foo.avi ! decodebin name=d .d ! ffmpegcolorspace ! theoraenc ! queue ! m. }

This will encode an avi file to an .ogg theora file. However, the above command is for files without sound. If you would need to convert files with sound, visit #gstreamer on irc at freenode.net and somebody there will help you out with sound commands.

---

### Post by xaque on 2005-08-10
After a few minutes of Googling, I found a program called [ffmpeg2theora](http://www.v2v.cc/~j/ffmpeg2theora/). It uses the ffmpeg library which is in the universe repository. I was looking to do the same thing myself, so I'll let you know how it works. From their website though, it looks to be command line only- no pretty GUI here :(

---

### Post by trigg on 2005-08-20
Here is a mini-Howto, but you definetly have to get your hands dirty - no pretty GUIs here.

[http://www.dogphilosophy.net/SECTION-Technical_Stuff/ogg-theora-microhowto.html](http://www.dogphilosophy.net/SECTION-Technical_Stuff/ogg-theora-microhowto.html)

---

### Post by phenest on 2007-12-17
Can anyone give an example of using mencoder to encode to theora (plus audio) please?

---

