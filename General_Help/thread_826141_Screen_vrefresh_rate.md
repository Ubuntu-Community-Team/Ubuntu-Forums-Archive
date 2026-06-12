---
title: "Screen vrefresh rate"
date: 2008-06-11
forum: General Help
---

### Post by cariboo on 2008-06-11
I've install fluxbuntu on an HP ze5475ca and I am having trouble getting X to work properly. It has an ATI IGP 330/M video apadter. The error in getting is **vrfresh out of range**. I've seen this problem before and it was fixed just using Ctrl-ALt-+, but this is a laptop and there is no seperate number keypad. Any help?

Thanks

Jim

---

### Post by ajmorris on 2008-06-11
> **cariboo907 said:**
> I've install fluxbuntu on an HP ze5475ca and I am having trouble getting X to work properly. It has an ATI IGP 330/M video apadter. The error in getting is **vrfresh out of range**. I've seen this problem before and it was fixed just using Ctrl-ALt-+, but this is a laptop and there is no seperate number keypad. Any help?

Thanks

Jim

Hi there,
have you tried reconfiguring Xorg (sudo dpkg-reconfigure -phigh xserver-xorg) to see if it sets your vertical refresh properly?

AJ

---

