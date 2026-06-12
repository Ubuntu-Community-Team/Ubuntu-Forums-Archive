---
title: "How to install ImageMagick 7.0 Q8?"
date: 2016-08-19
forum: General Help
---

### Post by m3rtijn on 2016-08-19
TLDR: How do I install ImageMagick 7.0 Q8?
It's as simple a question as that.

Just a plain ol' regular `apt-get install imagemagick` will get you 6.8.9.9 Q16.
If I can't have 7.0 (is it incompatible with Ubuntu 16.04 or something?), then at the very least I need Q8, to save memory on my server and get some more speed out of it. I don't need Q16 for anything, so it's quite a waste to use that.
On top of that, I need to use it in PHP, which can be achieved with the `php5-imagick` package just fine, but that too, will get you the Q16 version.

I don't see any way to choose between Q8, Q16 and Q32 anywhere. Not even saying anything about other variations...

I'm using Ubuntu 16.04.1 LTS.

---

### Post by coldraven on 2016-08-20
> I don't see any way to choose between Q8, Q16 and Q32 anywhere. What exactly are these Q numbers? I don't see any reference to them on the ImageMagick site.

---

### Post by m3rtijn on 2016-08-31
Quantization depth, if I recall. It's the number of bits used for each channel for internal processing of images. This means Q16 will use 64 bits per RGBA pixel, even if the source image is 32bpp. This makes it use an unneccesary large amount of memory and makes it slower - which is noticable on lower-end servers.

The purpose of making Q16 the default is, presumably, to reduce rounding errors when doing maths on the channel values. In my case however, all I (meaning a web application I'm running) use this library for, is scaling images. And for that, Q8 is leaner and faster, without producing any lesser images than with Q16.

Q32 is generally used as floating-point values for each channel, which is great for processing HDR images. Although Q32 with integers has its use-cases as well, for example to process high-bpp images from a camera.

Anyway, I'm looking for Q8.

Manual installation (downloading source, compiling, and all that goodness) I'd like not to do, because it makes it a PITA to update the lib easily with a simple set of apt-get commands.

---

### Post by coldraven on 2016-08-31
Maybe you just need to set  "limit" some values. 
[http://imagemagick.org/script/command-line-options.php#limit](http://imagemagick.org/script/command-line-options.php#limit)

---

### Post by slickymaster on 2016-08-31
*Thread moved to **General Help**.*

---

### Post by m3rtijn on 2016-09-01
No, that's different limits.

Quantization is hard-wired throughout the library, which is the reason it's compiled with either option (plus a couple more switches to suit one's needs, like float or int for Q32). It's not as simple as limiting the lib to some extend, it really does need a recompile. And that's why I originally asked where to install them from - reliably and updatable.

---

### Post by coldraven on 2016-09-01
> **m3rtijn said:**
> No, that's different limits.

Quantization is hard-wired throughout the library, which is the reason it's compiled with either option (plus a couple more switches to suit one's needs, like float or int for Q32). It's not as simple as limiting the lib to some extend, it really does need a recompile. And that's why I originally asked where to install them from - reliably and updatable.

OK I see what you mean now. In this post (link below) user Galeksic compiles Q 16
```
-DMAGICKCORE_QUANTUM_DEPTH=16
```

It looks like you will have to create your own PPA :(

[http://www.imagemagick.org/discourse-server/viewtopic.php?t=29006](http://www.imagemagick.org/discourse-server/viewtopic.php?t=29006)

---

### Post by m3rtijn on 2016-09-02
Well, there's a problem then...

I don't really have the time or know-how to set up something like that.
Also, knowing myself, it probably wouldn't be reliable at all :)

---

