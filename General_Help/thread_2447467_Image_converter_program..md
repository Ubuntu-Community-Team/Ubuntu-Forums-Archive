---
title: "Image converter program."
date: 2020-07-19
forum: General Help
---

### Post by xcfstarflight1 on 2020-07-19
Hi! I am trying to download XnConert, an image converter program. For some reason its No such package fond by apt, No package on either software center or snap. IT used to be. Anyone know how to get that program or if tgere are any other, New or ild that can von ert between most image file types?

---

### Post by Holger_Gehrke on 2020-07-19
XnConvert is closed source, commercial but free (as in beer) for private use. There is a .deb file available for download at [https://www.xnview.com/en/xnconvert/](https://www.xnview.com/en/xnconvert/) .

Alternatively you could just try ImageMagick. In the simplest case this involves just running something like 'convert oldname.bmp newname.png'. Of course there are literally hundreds of options to influence the conversion process. It's one of those tools you spend the rest of your life mastering.

Personally I've been using ImageMagick for years but wouldn't say I've mastered more than perhaps 10% of it's capabilities, it's just *that* powerful. Combine it with a bit of shell scripting and batch conversions (or watermarking, rotating,scaling or otherwise mangling images in myriads of ways) can be done really quickly. There's also lots of documentation and tips on using it on the web, so you almost never have to (re-)invent the wheel yourself, somebody somewhere has probably done something similar to what you're trying to do and has posted about it.

Holger

---

### Post by vmpx on 2020-07-19
Try [GIMP]("http://www.gimp.org/") (GNU Image Manipulation Program)

---

### Post by Yellow Pasque on 2020-07-19
GIMP's really heavy for simple image conversions. imagemagick or even ffmpeg should do the job and are probably already installed by default.

---

### Post by uninvolved on 2020-07-19
If you're interested in XnConvert, you can also just get XnViewMP and it has batch processing. It's closed source, but free for personal use (as mentioned above). I use it frequently and it actually installs from a .deb. There are many other tools to do this, including some with just terminal commands. I use XnView because I'm familiar with the layout and know where all the options are. If you're not familiar with it, there are probably better choices.

---

### Post by HermanAB on 2020-07-20
Maybe read this:
[https://linux.die.net/man/1/imagemagick](https://linux.die.net/man/1/imagemagick)

---

