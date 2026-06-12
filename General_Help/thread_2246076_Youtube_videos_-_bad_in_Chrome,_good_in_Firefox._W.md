---
title: "Youtube videos - bad in Chrome, good in Firefox. Why? How to fix?"
date: 2014-09-28
forum: General Help
---

### Post by Pelvur on 2014-09-28
Didn't watch Youtube much before, now started to find interesting stuff there. Noticed that it plays much better in Firefox for whatever reason. In below HD it is ok in chrome as well, but when I watch youtube HD video in chrome, it lags, freezes... fan starts to make lots of noise...  all that bad stuff. At the same time, other tabs in chrome work ok. Same video in Firefox - no problems, plays like a charm. 

I mostly use Chrome, so I would like youtube to work well in chrome as well. I would think it's hardware problem (my laptop is 9 years old) but the fact it works well in Firefox makes me think it's not a hardware. 

This refers to my D610 laptop (see signature).

Chrome version 37.0.2062.120, 
Adobe Flash Player - Version: 15.0.0.152
Shockwave Flash 15.0 r0

Firefox 32.0.3
Shockwave Flash 11.2.202.406
Shockwave Flash 11.2 r202

Did anyone have similar problems? Is there any fix for this (to make youtube work well in chrome as well)? I tried to search but didn't get much results other than unresolved complains on freezing youtube in both browsers. 

Thanks.

---

### Post by Pelvur on 2014-09-29
I found out interesting thing - it is not Flash Player responsible for playing most of the videos in Youtube on Chrome, but HTML5 player. So I disabled HTML5 in chrome, but that didn't help much, the video is still lagging a lot.

---

### Post by nerdtron on 2014-09-29
Chrome>Settings> Search for "hardware" on the search settings box.
Is there an option for "Use hardware acceleration when available"? Is it checked?

---

### Post by vasa1 on 2014-09-29
> **nerdtron said:**
> Chrome>Settings> Search for "hardware" on the search settings box.
Is there an option for "Use hardware acceleration when available"? Is it checked?Good point. On the settings page, OP will need to go right to the bottom and click on "advanced settings" and then near the bottom of the new page see, under System Settings, whether "hard acceleration" is checked or not.

On my system, which has only integrated graphics and no gpu, that setting is unchecked. I keep it off in Firefox as well.

---

### Post by nerdtron on 2014-09-29
Don't forget to restart Chrome/Firefox when you enable/disable this feature. Just to make sure it is applied.

---

### Post by vasa1 on 2014-09-29
There's a good chance hwa needs to be disabled given the age of OP's laptop. OP, do you have a cpu usage monitor installed. I think if you use a laptop, having an always visible CPU monitor could be informative.

---

### Post by Pelvur on 2014-09-30
Thanks for suggestion. The hardware acceleration was indeed checked, and I unchecked it and restarted Chrome.  Did not see any improvement.

---

