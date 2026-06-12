---
title: "Gstreamer."
date: 2007-07-01
forum: General Help
---

### Post by phizikal on 2007-07-01
Ok, I have dapper. I am not getting no sound what-so-ever. I know I have a sound card and all that goody. But under my "volume control" I am getting this error.

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

I went under my synaptic package manager and it says I have it. I am guessing it is outdated or what? 

If anyone know how to fix this please help.

---

### Post by jwh400 on 2007-07-01
In synaptic select "Advanced" and search for gstreamer. Scroll down and make sure "ALSA plugin for GStreamer" is installed.

---

