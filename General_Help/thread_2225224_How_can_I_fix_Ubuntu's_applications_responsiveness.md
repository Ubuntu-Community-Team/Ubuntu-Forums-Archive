---
title: "How can I fix Ubuntu's applications responsiveness?"
date: 2014-05-20
forum: General Help
---

### Post by nubela on 2014-05-20
The responsiveness is really bad on the fresh install of 14.04 on my really state-of-the-art laptop?

Here's the specs of my laptop:

Quadcore Intel i7-4600U CPU @ 2.10GHz 12GB Ram 1TB Samsung EVO SSD

And when gradle is compiling, my entire system slows to a crawl, videos begin stuttering, browser scrolling lags, etc.

The same goes when a page refresh occurs in another window in Chrome, and while it refreshes, the HTML5 video in another tab begins stuttering.

How can I fix this?

---

### Post by Impavidus on 2014-05-20
Have you checked for proprietary drivers? State-of-the-art hardware often has no good open source drivers (yet). Search for the "additional drivers" tool. I'm not sure where exactly; I use Xubuntu.

---

### Post by Gyokuro on 2014-05-20
How about to pin gradle to a certain CPU via taskset ([http://manpages.ubuntu.com/manpages/trusty/man1/taskset.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/taskset.1.html)) to keep your system smooth?

---

### Post by mcduck on 2014-05-21
...or set it's "nice" value higher to make it lower priority than rest of your aplications. Check the "nice" and "renice" commands.

---

