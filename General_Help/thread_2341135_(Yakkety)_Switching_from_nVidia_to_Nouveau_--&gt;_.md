---
title: "(Yakkety) Switching from nVidia to Nouveau --&gt; Black screen after GRUB"
date: 2016-10-25
forum: General Help
---

### Post by amano on 2016-10-25
I had a strange thing recently:

I updated to Yakkety (not a smooth upgrade though, I had to fiddle around a lot and install things manually because of some .Xauthority related problems) and wanted to try out the new Unity8 session. Unity7 was working fine.

The new Unity8 wouldn't let me log in. I investigated a bit and it seemed possible that me using the nVidia drivers might have been the problem. So I went into my Unity7 session and to the proprietary driver settings and unchecked nVidia. Then I rebooted.

After GRUB the screen suddenly went black. But it was not just a black screen, the monitor turned even off, not getting any signal at all.

Is it possible that my ION 330 chipset (within the ASRock ION330) isn't still supported at all in nouveau/the 4.8 kernel?

Does anybody have nouveau and this chipset working in Yakkety??



I have been on the nVidia driver for many years and the problem might have persisted even before.

I could fix the problem to get to lightdm and into the Unity7 session by using the Ubuntu safemode options this time. There I activated nVidia again before the next reboot. I am quite frightened that I cannot get to the console the next time to revert things.

---

