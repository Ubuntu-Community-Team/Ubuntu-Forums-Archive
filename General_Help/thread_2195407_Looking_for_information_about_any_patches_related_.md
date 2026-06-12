---
title: "Looking for information about any patches related to Radeon DPM in the Ubuntu kernel"
date: 2013-12-23
forum: General Help
---

### Post by HittingSmoke on 2013-12-23
First of all, apologies that this isn't directly Ubuntu related but I'm at the end of my rope in resources here and I thought maybe someone here could help me.

Here's the deal. I'm running a GPU (HD4870) which was marked legacy by AMD so I can't use FGLRX unless I want to use xorg < 1.13. Therefore I'm pretty much stuck with Radeon on any recent distro. The radeon driver is pretty much unusable without the dynamic power management patch introduced in kernel 3.11. Performance is worse and the fan speed at idle is atrocious. So I require the radeon driver with DPM using kernel > 3.10. I had this working fine in Ubuntu 13.10. It was my first return to Ubuntu since before Unity and I'm not a fan of Unity. Nothing against it personally, it's just not for me. I've always been a KDE fan.

So I switched to Debian (please bear with me, this is not a Debian support request) testing for the 3.11 kernel and Steam library support. Unfortunately with the Debian 3.11 (and 3.12, and 3.12 Liquorix) kernel the system hard locks then (sometimes) throws up a machine check exception at boot if I have DPM enabled and two monitors plugged into my card. If I disable DPM or unplug one of my monitors the system boots fine and DPM is perfectly functional in the radeon driver. If I install the 3.11.9 Ubuntu mainline kernel I had running in Ubuntu 13.10 on my Debian Jessie install then the system boots fine with functioning DPM when both my monitors are connected. So this leads me to believe there's some patch in the Ubuntu kernel which fixes this issue or there's a patch in the Debian and Liquorix kernel which breaks it.

The reason I'm posting this here is I'm at about the extent of my knowledge with this issue. So far no Debian volunteer support has been able to help with this. What I'm hoping is that someone here is knowledgeable enough about the nuances of the Ubuntu-specific kernel patches to tell me what Ubuntu-specific patches related to Radeon DPM might be causing the Ubuntu kernel to work flawlessly with this setup while all other kernels seem to be failing at it. I tried to browse the Ubuntu kernel patch notes for information related to DPM but it's a bit over my head. Most entries seem to be about "disk pool management" where I'm looking for "dynamic power management" related to the radeon driver.

Does anyone who's well versed in the Ubuntu kernel have any insight which might help me find the difference between the kernels that's causing the issue?

---

