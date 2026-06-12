---
title: "Audio Not Functioning After Botched Virtualbox Install"
date: 2008-05-17
forum: General Help
---

### Post by Starmage187 on 2008-05-17
Hello. I've got an install of Hardy Heron on my notebook, and I'm hoping that some one here can help me salvage it. I had everything working fine on it, but I needed virtualization software. I installed Virtualbox via apt-get, but it didn't grab the kernel header packages, and so it was useless. I removed it, and used Synaptic to get all of the packages, but even though I know it downloaded and installed the kernel-header package, I got the exact same error. Actually, once I installed those packages via synaptic, it was as if I had never removed it in the first place (created virtual machines were still there, preferences, etc) and so I consulted a friend of mine who is more familiar with Ubuntu then I am. 

He removed all of the cached debs, and when the computer rebooted, my wireless was not active, nor was my sound device detected by gstreamer. LSPCI sees it, however. 

Updates and some tweaking have restored my wireless, but my audio is still inoperative, which means all multimedia is pretty much busted. 

Does anyone have any ideas?

If you need anymore information, just ask. Thank you in advance.

---

