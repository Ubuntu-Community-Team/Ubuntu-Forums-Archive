---
title: "Where's all my RAM going?"
date: 2007-12-16
forum: General Help
---

### Post by ~LoKe on 2007-12-16
[Image for reference](http://fc05.deviantart.com/fs24/f/2007/350/0/d/Desktop_as_seen_on_12_16_07_by_IcedLoKi.jpg).

Note conky on the bottom, saying 950/1.98.

Now, I don't really understand what's happening here.  Firefox open, no tabs (around 850-890 with FF closed).  Screen/rtorrent/bash/bash/irssi.

That's all.

Oh, and my WM is DWM, which is supposed to be very light-weight.

So...where's all my ram going?

---

### Post by mcduck on 2007-12-16
Mostly it's used as cache for disk reads/writes to improve performance. Memory not used is memory wasted. Them if programs need more memory some cached data is just dropped.

To check your real memory usage run 'free -m' in a terminal, and read from the "+/- buffers/cache"-line. This will tell you how much memory programs are using.

---

### Post by ~LoKe on 2007-12-16
> **mcduck said:**
> Mostly it's used as cache for disk reads/writes to improve performance. Memory not used is memory wasted. Them if programs need more memory some cached data is just dropped.

To check your real memory usage run 'free -m' in a terminal, and read from the "+/- buffers/cache"-line. This will tell you how much memory programs are using.

Didn't know about free -m!  Thanks!

---

