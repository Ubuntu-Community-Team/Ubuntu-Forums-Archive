---
title: "how to convert gif image to avi?"
date: 2007-05-03
forum: General Help
---

### Post by tubunu on 2007-05-03
How can a gif image be converted to avi, mov or mpeg? Thank you.

---

### Post by sinfree on 2007-05-09
You should be able to use ffmpeg from the command line to do that.  It should be installed by default, if not just use Synaptic (System -> Administration -> Synaptic Package Manager)  and just search for ffmpeg to install it.

Try these lines in the terminal (obviously replace test.gif and test.avi with whatever you want):

```
convert test.gif test%05d.jpg
ffmpeg -r 5 -i test%05d.jpg -y -an test.avi
```

The first line should give you a collection of jpegs (1 for each frame of the gif).  The second line actually puts it as an avi.  You can edit any of the jpegs before the conversion if you need to edit a frame.  The -r 5 is the rate, which you can change as needed.

You could potentially just use the ffmpeg to do the whole coversion in one line (without having to do the jpeg part), but your success may very with that method.

Check out this forum topic for details:

[http://www.linuxquestions.org/questions/showthread.php?t=549839](http://www.linuxquestions.org/questions/showthread.php?t=549839)

---

### Post by marufaberlin on 2008-03-09
That method worked, thanks, but I get extremely low quality:(. The jpegs alone are OK, but the ffmpeg output is low in quality. Is there a command line parameter I could pass to ffmpeg so that I get satisfying quality? Thanks in advance.

---

