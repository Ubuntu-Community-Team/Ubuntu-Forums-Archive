---
title: "Outputting EasyCap video to a stream"
date: 2014-10-18
forum: General Help
---

### Post by cable_guy on 2014-10-18
Hi all,

I'm looking for some help please on whether something is possible.

I have this device

 [IMG]http://i.ebayimg.com/00/s/NjAwWDYwMA==/z/rd0AAOSwBvNTnipF/$_3.JPG[/IMG]

which takes phono from my security camera and passes it to USB, with Windows I can see the output of the video camera, and Ubuntu recognises it (and some chap in this guide [http://www.serkey.com/ubuntu-easycap-on-linux-guide-bd45d3.html](http://www.serkey.com/ubuntu-easycap-on-linux-guide-bd45d3.html) has managed to make more of this device)

So I'm wondering if the video device that this hardware presents to Ubuntu is possible to convert to a real time stream, which I can access from web browsers across my network?

Can anyone think of a way that can be done, or even start me off in the right direction please?

---

### Post by HermanAB on 2014-10-18
Read the ffmpeg help file.  Google will find it.  

You can serve streams with ffserve.

You also need to read the route man page, since you will need to configure a default route for multicast streams.  There is an example in this man page.

Finally, you can test the playback with ffplay.

---

### Post by cable_guy on 2014-10-18
thanks so much, i'll check out ffmpeg now.

Regarding a "stream", maybe I have my terminology wrong, I was thinking that perhaps I can host the stream on the box which is capturing and just access it through worst case a web browser, or best case a plugin to XBMC!

---

