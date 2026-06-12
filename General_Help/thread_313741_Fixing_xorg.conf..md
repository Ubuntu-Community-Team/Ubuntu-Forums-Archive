---
title: "Fixing xorg.conf."
date: 2006-12-06
forum: General Help
---

### Post by IncomingFire on 2006-12-06
So I had f'ed up my xorg.conf apparently.  Full story and explanation here: [http://linuxtravels.blogspot.com/2006/12/i-wtfed.html](http://linuxtravels.blogspot.com/2006/12/i-wtfed.html)

After a little playing around I was able to get it working again.

If xorg goes completely whack on you try this combo:

From terminal:
sudo dexconf

then

sudo dpkg-reconfigure -phigh xserver-xorg


Hope this helps someone thats having problems.

---

### Post by acb5430 on 2008-01-28
Thank you for this fix! I recently edited my xorg.conf file, and in my infinite wisdom failed to back it up. It was a long line of changing screen resolution that rendered the file unusable, but thanks to this fix, I can now spare myself the hassle of reinstallation. Again, thanks for posting this!:KS

---

