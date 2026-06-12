---
title: "vlc crashes on selection of 3d spectrum visualization"
date: 2016-11-01
forum: General Help
---

### Post by wyndlass on 2016-11-01
i'm still usin 15.10. i currently have no way to do a backup so i haven't upgraded yet. i'm on a hp pavilion g7-2017 intel i3 6gb ram approx 650gb hdd. when i listen to music and want to use the 3d spectrum visualization. vlc crashes. i don't remember when this first started. i kept forgetting to do a search on this and finally did and didn't see anything that helped with the problem. if anyone can help with this, thanx.

---

### Post by mc4man on 2016-11-02
Try, Tools > Preferences > Input/Codecs > Hardware-accelerated decoding > set to Disabled, click save
(- or if using an Intel gpu you can try picking one of the VA-API options, though it may only work for a short period of time before causing a race & lockup.
Better to just disable until vlc gets smarter, if ever..

---

### Post by wyndlass on 2016-11-04
> **mc4man said:**
> Try, Tools &gt; Preferences &gt; Input/Codecs &gt; Hardware-accelerated decoding &gt; set to Disabled, click save<br>
(- or if using an Intel gpu you can try picking one of the VA-API options, though it may only work for a short period of time before causing a race &amp; lockup.<br>
Better to just disable until vlc gets smarter, if ever..<br><br><br>



i'll try your suggestions. hope it works. thanx.

---

