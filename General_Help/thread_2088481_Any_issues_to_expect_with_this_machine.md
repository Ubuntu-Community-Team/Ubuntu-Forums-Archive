---
title: "Any issues to expect with this machine?"
date: 2012-11-26
forum: General Help
---

### Post by weasel fierce on 2012-11-26
We just ordered a laptop from dell. Inspiron 17R, has an I3 processor and Intel 4000 graphics chip. How are drivers for the intel graphics?

Anything to be concerned about? (it'll run Kubuntu rather than Ubuntu in the end)

Cheers!

---

### Post by LiamOS on 2012-11-26
I've never had graphics trouble with linux(Ubuntu,Gentoo,Linux from Scratch), and my i3 machine behaves very well processor-wise. I wouldn't expect any issues with that machine, but there's always a small chance of getting a not-fully-supported wireless card... Even then it should still work OOTB on Ubuntu.

---

### Post by jualin on 2012-11-26
Yeah, modern Dell laptops have become pretty standard and the Intel graphics should be pretty compatible according to [Proronix]("http://www.phoronix.com/scan.php?page=article&item=intel_hd4000_ivybridge&num=1"). I installed Ubuntu on a Dell 15R last week with everything working out of the box. You should be fine :)

---

### Post by weasel fierce on 2012-12-01
Got the machine and it's awesome :)

Wireless, web cam, it all works without fuss

---

### Post by jualin on 2012-12-01
> **weasel fierce said:**
> Got the machine and it's awesome :)

Wireless, web cam, it all works without fuss

That's great! Enjoy it :)

---

### Post by weasel fierce on 2012-12-01
best of all, now my wife is learning Kubuntu :) She's already enjoying the customization and how we can each have our own look and feel

---

### Post by boogerama on 2012-12-01
You may run into issues with the Broadcomm wireless drivers. The fix is fairly straight forward.  

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer

That's always worked for me.

---

### Post by weasel fierce on 2012-12-01
Appreciate the heads up. So far the wireless has been completely stable :)

---

