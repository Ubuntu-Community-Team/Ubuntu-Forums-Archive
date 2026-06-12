---
title: "Display problems with Unity in Ubuntu 13.04"
date: 2013-05-29
forum: General Help
---

### Post by NautiusMaximus on 2013-05-29
I'm having some odd display problems. My screen is covered in purple patches. The attached screenshot shows what I mean.

I can work around the problem by installing the gnome-session-fallback and then logging into Gnome fallback with no effects. If I log into standard Gnome, I get the same problem as in Unity (although possibly not quite as bad).

However, this is not a great workaround, as I like Unity, and don't really want to give it up.

I'm using an Nvidia graphics card, with the default non-proprietary drivers (X.Org X server). I did try to fix this problem by using the proprietary Nvidia drivers (nvidia-310). This did get rid of the purple patches, but it also completely rogered my Unity interface. All my launcher buttons and everything else was gone: I just had a blank screen with my background picture. I could call up a terminal with ctrl-alt-T, and launch programs from the terminal, but that was it.

Any ideas what I could try to get Unity working again?

Thanks
NM

---

### Post by dino99 on 2013-05-29
do you get that issue with "nouveau" also ?
maybe its related to some compiz option(s)
[http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04](http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04)

compiz --replace ccp &
setsid unity

---

### Post by NautiusMaximus on 2013-05-29
Thanks, but the post you link to talks about reverting to default settings. I don't think that can be the problem here, as I'm having these problems with a fresh install.

---

### Post by bela42 on 2013-05-29
Could be that compiz (or the unity plugin) is crashing when you use the proprietary driver. Try to run compiz --replace from the terminal, this may give you some error messages.

---

### Post by NautiusMaximus on 2013-05-30
Oh, thanks for that suggestion. Should I try that while using the proprietary driver or the default?

---

