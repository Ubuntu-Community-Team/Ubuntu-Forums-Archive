---
title: "CPU usage low, temperature high"
date: 2015-06-21
forum: General Help
---

### Post by chrisf1874 on 2015-06-21
Upgraded to 15.04. I think it's  related to audio because I first had serious problems when using Ardour.
Starting with the 3.16 kernel fixes the problem completely.

Core temperatures when playing a youtube video using the 3.19 kernel rise to mid 70s within a couple of minutes with cpu activity very low.
Can't insert an image here for some reason so here's a [link]("https://www.dropbox.com/s/8vjfmq6io3l3pkh/Selection_441.png?dl=0").
Prolonged video playback leads to cpu throttling.

Using kernel 3.16 does not result in any temperature [rise]("https://www.dropbox.com/s/8s2ects9xqzt2yh/Selection_443.png?dl=0").

Using the 3.19 kernel, just playing an MP3 file makes core temperature [rise ten degrees]("https://www.dropbox.com/s/xbir0o5slyuy60k/Selection_445.png?dl=0").

I've tried kernels v3.19.1, v3.19.8 and v4.0.0 and all show the same problem.

I'm using 15.04 on an Acer Aspire V3-771 with Intel® Core&#8482; i7-3632QM CPU @ 2.20GHz × 8 and 8GB of ram.

---

