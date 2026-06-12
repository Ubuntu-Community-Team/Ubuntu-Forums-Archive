---
title: "Compiz interferes with video and other programs"
date: 2008-05-17
forum: General Help
---

### Post by darthpenguin on 2008-05-17
Hello All,
I have been having issues with compiz (or compiz fusion I don't know which one I have). I find that when Compiz is enabled some programs such as Celestia or Stellarium are choppy and slow. Also VLC will not play video, instead I hear audio but see a green screen within the VLC window. Sometimes VLC will play video while compiz is running but I will see an annoying horizontal line across the middle of the video (as if if is running at a low refresh rate). If I switch to Metacity from the compiz tray icon all is well. I could just forget comiz all together but I would like to have the eye candy if I can have it run smoothly with the rest of my system. Has anyone else had this problem? is there any solution?

I am running Ubuntu 7.10 on a;
AMD Sempron 3400+
512 MB DDR RAM
EVGA e-GeForce 7200 GS PCI Express

---

### Post by markbuntu on 2008-05-17
Check to see if compiz is using indirect rendering and if it is then that is the problem. It is a problem with a GLib_pixmap call that either the driver makers or compiz need to fix before compiz will use direct rendering. 

As it is, if you run the benchmark in compiz you will see very low fps at max cpu usage and that is what is messing up the video playing and everything else that needs fast fps.
On my system I get about 30-50fps with compiz and about 4300 without and that is with dual monitors. 

Google Earth, among others flashes with compiz.

Ubuntu Hardy 8.04 386i
AMD Athlon64 3800+
3GB RAM
ATI 3650 PCI Express w 1GB RAM
ATI restricted driver 8.47.3

I think I saw some post around here about nvidia restricted drivers supporting compiz direct rendering but I cannot tell you for sure about that. If so, that would fix your problem. Us ATI owners will just have to wait.

---

### Post by tommyhakinen on 2008-05-18
Cek if you have direct rendering. Open Terminal then type:
> glxinfo | grep 'direct rendering'

If the reply is NO, most likely it's most likely your Graphic Card's driver. Go to System > Administration > Restricted Driver.

Install the driver for your Graphic Card. That should be okay.

Regards,

tommy

---

### Post by darthpenguin on 2008-05-18
Thank you for your replies,

I do not know what Direct Rendering is and when I type "glxinfo | grep 'direct rendering' I get a reply "direct rendering: Yes"

any other ideas?

---

