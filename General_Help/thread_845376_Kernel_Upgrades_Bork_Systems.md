---
title: "Kernel Upgrades Bork Systems"
date: 2008-06-30
forum: General Help
---

### Post by JLucien on 2008-06-30
I have kernel upgrade issues on two different boxes, and would like some advice on how to handle them.

On my main desktop, Ubuntu Gutsy running 2.6.22-14-generic kernel, an upgrade to 2.6.22-15-generic makes my system run in low graphics mode.  Why is that? My first port of call to fix it would be to reinstall the graphics driver but I don't see why I should have to do that if it's already installed, so I'm trying to understand what happened there.

On my eeepc, which is running eeeXubuntu, same kernel, same upgrade rendered my networking, both wired and wireless, completely unresponsive, and again I don't know why.  I even used a wired connection and gave it a static address but it still couldn't ping my switch.

Have I just had bad luck here or are kernel upgrades to be looked at with trepidation?

Cheers :)

---

### Post by avtolle on 2008-06-30
Depending on how the graphics driver was installed (e.g., manual install of the driver downloaded from the vendor's site), it is necessary to reinstall the driver when there is a kernel upgrade. Same applies for wireless drivers.

---

### Post by russlar on 2008-06-30
> **JLucien said:**
> On my main desktop, Ubuntu Gutsy running 2.6.22-14-generic kernel, an upgrade to 2.6.22-15-generic makes my system run in low graphics mode.

I ran this update on my thinkpad t61 with intel graphics a couple of weeks ago, and had no problem. oddly enough, I have this problem if I try hardy.

---

