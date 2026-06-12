---
title: "Codecs and Containers"
date: 2014-07-10
forum: General Help
---

### Post by Tighe on 2014-07-10
Hi There,

I am currently putting together various containers in order to properly play videos for my site on every OS and browser available. We are going to most likely be running three different containers: MP4, WebM and OGV. My question is what video and audio code combinations should I consider combing with these in order to create the best possible video formats? Also, if anyone can touch on the licensing issues behind using MIRO to encode MP4 containers, that would be much appreciated. Here are the [legal videos]("http://www.locallawyerguide.com") I'm referencing. Thank you in advance!

- Tighe

---

### Post by TheFu on 2014-07-10
h.264/AAC/mp4 seems to have won the war of codecs and containers for the vast majority, even if the MKV container **is** actually better thanks to nearly infinite flexibility.

What about VP8 or is that part of webm?

Don't think I've ever seen webm or ogv anywhere except pirated content from Asia.

h.264 video decoders are free for worldwide use - the group behind it decided it was better to give the decoder away than lose the encoder licensing completely. [http://www.mpegla.com/main/programs/AVC/Pages/FAQ.aspx](http://www.mpegla.com/main/programs/AVC/Pages/FAQ.aspx)  I believe a commercial-use license is still required to create h.264 content.

---

### Post by at_first_light on 2014-07-16
I agree with TheFu H.264 video + AAC audio all wrapped up in an MP4 container is the best option for the web. It's highly compatible and gives great quality. If it wasn't for the compatibility part I prefer MKV over MP4 containers because it's less limiting in terms of what you can put in it.

---

