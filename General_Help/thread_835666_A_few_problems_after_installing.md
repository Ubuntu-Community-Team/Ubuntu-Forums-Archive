---
title: "A few problems after installing"
date: 2008-06-20
forum: General Help
---

### Post by Boompat on 2008-06-20
Hi, I installed Ubuntu 8.04 yesterday, and a few problems came up.
1. At some random websites, Firefox quits. I'm not sure what's causing this problem, but from what I can tell, it quits on sites that require flash.
2. With Pidgin, I get timeouts very quickly when using MSN Messenger. It works fine with the others, though.
3. At very random moments, my mouse will go crazy and jump to different spots on the screen for a couple seconds. This results in the trash opening up in 3 different screens, or the power down screen popping up a bunch of times.

If it helps, I'm using an IBM Thinkpad R31. Any help would be appreciated.

---

### Post by Wobblybob on 2008-06-20
> **Boompat said:**
> Hi, I installed Ubuntu 8.04 yesterday, and a few problems came up.
1. At some random websites, Firefox quits. I'm not sure what's causing this problem, but from what I can tell, it quits on sites that require flash.


you could add the flashplugin-nonfree via [System], [Admin...] Synaptic Package Manager] which may sort this problem. If your mouse problem is a touchpad problem rather than a mouse I would do a search as I think others have had this problem with Hardy.

---

### Post by Boompat on 2008-06-20
> **Wobblybob said:**
> you could add the flashplugin-nonfree via [System], [Admin...] Synaptic Package Manager] which may sort this problem. If your mouse problem is a touchpad problem rather than a mouse I would do a search as I think others have had this problem with Hardy.

I've already downloaded the flashplugin-nonfree. Also, it's not a touchpad. It's one of those red dot things that come with IBM laptops.

---

### Post by avtolle on 2008-06-20
Check to be sure that gnash (the open-source flash project) and its plugin are not installed; if they are, then in Synaptic mark them for complete removal, apply, this to avoid conflicts between the two flash apps.

---

