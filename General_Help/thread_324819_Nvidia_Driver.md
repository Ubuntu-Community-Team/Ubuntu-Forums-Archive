---
title: "Nvidia Driver"
date: 2006-12-24
forum: General Help
---

### Post by lexus_is250_awd on 2006-12-24
First off...I'm new to linux but, It seems though people make it so hard to load nvidia drivers.
Maybe I'm not loading mine correctly but it's working for me. All I did was add repository:

[http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable

reloaded packages and searched for nvidia in synaptic and downloaded driver version 9746 then sudo nvidia-xconfig. Restarted and nvidia logo splahscreen comes up and all good. I can play games whoohoo!!!

I've seen some how-to's that'll make your head spin. Am I doing this right is my question? And what is XGL? How can I tell if I have it or if it's enabled? And how about 3d accelleration?

Thanks!!!

---

### Post by fragos on 2006-12-24
Ubuntu includes an nvidia driver in their repositories.  Run Synaptic and install nvidia-glx.  This will be a different version of driver than you installed but it works fine.  To check if 3D is running, do "glxinfo |grep rendering" in a terminal window. 3D running will respond "direct rendering: Yes".

---

### Post by lexus_is250_awd on 2006-12-24
Thanks!! 3d acceleration is enabled. Cool!!

---

