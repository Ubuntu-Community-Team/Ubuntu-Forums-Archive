---
title: "Video Choppy After Upgrade to Hardy"
date: 2008-04-29
forum: General Help
---

### Post by metalgtr on 2008-04-29
Hi all,

[UPDATE] I have found that this problem was just solved in another post: [http://ubuntuforums.org/showthread.php?p=4839684#post4839684](http://ubuntuforums.org/showthread.php?p=4839684#post4839684)

I just upgraded to Hardy 8.04 from Gutsy 7.10 and now all my video is choppy. My system monitor shows that XGL is using a high % CPU. Compiz and effects are working, but extremely choppy - whereas they previously worked smoothly on gutsy.

I have searched the forums and seen that people with ATI's are having some similar problems - so here is what I have:


$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


And...

$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

I also have two restricted drivers in use: 
ATI accelerated graphics driver
Software modem


I hope this is enough to help and easy to fix - any help is appreciated.
Thanks everyone!

---

