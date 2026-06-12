---
title: "X265 encoding on Linux vs Windows, Why windows is faster?!"
date: 2021-08-03
forum: General Help
---

### Post by kamyd on 2021-08-03
Hello Everyone, I have always wanted to switch to linux as my main operation system but unfortunately each time I test it, its performance is way lower than windows, so I have to always use it in VM or dualboot (need it for ML)

So I wanted to ask why is it like this? 

Here is a simple test of handbrake X265 encoding:
(This test was for my personal reference so, sorry about quality)

-freq+voltage offset+power limit are manually set in both (throttlestop and throttled)
-handbrake version is the same version
-kernel 5.13
-For both mitigations are turned off.

[[img]https://i.postimg.cc/VJ4kGY67/20210721-181857.jpg[/img]](https://postimg.cc/VJ4kGY67)

[[img]https://i.postimg.cc/yJdY2w37/20210722-102313.jpg[/img]](https://postimg.cc/yJdY2w37)

And in linux when I turn off mitigations the performance barley changes (like 1 second in 7 minutes) but on windows the difference is huge (8.04 second vs 6.98) why is that? Am I doing something wrong here?!

Cpu is 9750H and I am using mitigations=off.

---

### Post by ActionParsnip on 2021-08-03
It's just over 1 second more.....is this "huge" ?

---

### Post by kamyd on 2021-08-03
What is 1 second more?!
Windows encodes in 6 minutes and 58 seconds.
Linux encodes in 7 minutes 19 seconds.
Is this a 1 second difference or 21 seconds of difference?!
And I should remind you that its 21 second in 7 minutes of encoding think of the huge difference when you encode for 50hrs.

---

### Post by HermanAB on 2021-08-03
Which x265 codec are you using? The VideoLAN one is pretty good: [https://www.videolan.org/developers/x265.html](https://www.videolan.org/developers/x265.html)

---

### Post by TheFu on 2021-08-03
MS-Windows has a $2.15T company behind it, with a single vision.

Linux has about $1B behind it from 250 different companies, each doing their own stuff, as they like, separately.  We have lots of choices, thanks to this. We don't have a single vision, that's the downside.  Proprietary GPU companies want to be paid for their efforts. nVidia charges for software now.  That will never work for free Linux distros to include those capabilities.

If you automate the encoding, those slight differences really won't matter.  I use TaskSpooler to push jobs into a queue so only 1 runs at a time, but the system is always busy.  I also set the task priority to be low, so any other task I'm doing doesn't feel slow, ever.  Batch stuff can take hours, day, if it likes.  I don't care.

My playback devices don't support h.265, so I haven't done much beyond play encodes.  h.264 will be used here for a few more years.

---

