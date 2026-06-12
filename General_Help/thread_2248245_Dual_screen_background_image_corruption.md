---
title: "Dual screen background image corruption"
date: 2014-10-13
forum: General Help
---

### Post by dfrandin on 2014-10-13
I am running Ubuntu/Kubuntu 14.04/64 bit with an Nvidia Quadro FX580 video card/Nvidia 331.38 "blob" driver and dual screens. All works fine EXCEPT for the fact that, frequently, after coming out of sleep/standby, one of the screens will have the attached pattern on it. If this occurs on the primary screen, configured to show the desktop folder, I don't see any of the icons that should be there, however any programs started work just fine, including things like gkrellm (a corner of which you can see in the screen shot). In short, everything works fine except for the weird corrupt background. It has never occurred on both screens at the same time, just on one or the other. If I ctl-alt-bksp and restart Xorg, the problem goes away, and may not reappear the next time the system comes out of sleep/standby. I use sleep/standby extensively to conserve power when I'm not using the system.. Any ideas? 

[ATTACH=CONFIG]257184[/ATTACH]

Update: Since the system was originally installed as standard Ubuntu, with KDE added via metapackage, I decided to see if the screen corruption occured in Unity.. Interestingly, it does not.. I tried sleeping/waking the system quite a few times while using Unity, and never saw any screen background corruption.. So apparently this is a KDE issue rather than a basic Nvidia graphics issue... I'd stay on Unity but for the fact I detest Unity, which was why I installed KDE. Since nobody here seems to have any ideas, I guess I'll post the issue on the KDE forum..

---

