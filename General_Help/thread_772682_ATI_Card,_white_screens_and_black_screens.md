---
title: "ATI Card, white screens and black screens"
date: 2008-04-28
forum: General Help
---

### Post by Traceur-UK on 2008-04-28
Right, I recently upgraded to Hardy Heron and started using Ubuntu as my primary OS again. I really want to get Compiz Fusion working, but I'm running into two large issues. They are as follows:

On enabling the desktop effects, I get a white screen. However, by installing xserver-xgl I can get it working, it just runs at a ridiculously slow FPS.

When I try to enable my ATI Card (ATI Radeon 9600) it gets past the splash screen, and then I simply get a black screen. ctrl+alt+f1, f2 etc do nothing.

Are there any solutions to my problem? I remember it working fine a few months back before I reinstalled everything, in Gutsy Gibbon. It worked a treat. Now it doesn't in Hardy Heron.

Can anyone help me?
Thanks in advance.

---

### Post by sco01 on 2008-04-28
Got the same problem. A Thinkpad T42 with: 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]. It Worked fine in 7.10 and then i upgraded...

---

### Post by Traceur-UK on 2008-04-28
I've been reading around and as far as I can tell, the black screen is something to do with new proprietary ATI drivers. Or something. However, from the ATI site, I tried installing some older ones and still no luck. Perhaps it's something to do with the drivers not liking an update in Hardy or something... This also presents a problem as I can't run any 3D games. I tried Chromium as my test (as I always do) and it's laggy. Without the ATI drivers, I'm stuck.

---

### Post by Traceur-UK on 2008-04-29
Bring
Up
My
Post

---

### Post by sco01 on 2008-04-29
I poked around a lot yesterday and got it to work eventually. I'm not 100% sure about how I did it but it included:

Uninstall the proprietary ATI driver (It caused the screen to flicker and behaved weirdly).
The SKIP_CHECKS="yes" "hack".
Re-install compiz.
Reboot.

The machine is now in a state similar to before the upgrade. It looks to me like the upgrade routine in Hardy is broken somehow. I would like to know if somebody has had similar problems after a fresh install of Hardy on a Thinkpad T42?

---

### Post by Saint Angeles on 2008-04-29
white screen means direct rendering is not enabled...

i have a mini-tutorial for installing the latest ATI driver here...

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

good luck!

---

### Post by Traceur-UK on 2008-04-29
Still no luck with that tutorial.
With xserver-xgl installed:
installing and 'aticonfig --initial' - black screen after load
installing without aticonfig --initial - desktop effects can be enabled, but insanely laggy (same problem as before, as if i never installed the drivers)

WITHOUT xserver-xgl installed:
installing and 'aticonfig --initial' - black screen after load
installing without aticonfig --initial - white screens upon desktop effects or compiz --replace.


How would I go about turning direct rendering on?

---

### Post by CarnivorouZ on 2008-04-29
I have the same issue and I have been going back and forth with people on this forum for a few days trying to figure it out.  Good luck to you too.

[HTML]http://ubuntuforums.org/showthread.php?t=768713[/HTML]

---

### Post by Saint Angeles on 2008-04-30
> **Traceur-UK said:**
> Still no luck with that tutorial.
With xserver-xgl installed:
installing and 'aticonfig --initial' - black screen after load
installing without aticonfig --initial - desktop effects can be enabled, but insanely laggy (same problem as before, as if i never installed the drivers)

WITHOUT xserver-xgl installed:
installing and 'aticonfig --initial' - black screen after load
installing without aticonfig --initial - white screens upon desktop effects or compiz --replace.


How would I go about turning direct rendering on?
ok dont use xgl... ati doesnt need it anymore.

the white screen means compiz works but direct rendering is not enabled. you need to do what is in my tutorial but trying different fglrx (proprietary ati) drivers. the link i posted was for the latest but sometimes an older one will work instead. the aticonfig --initial... command just puts a couple lines under the "device" section of your xorg (lines that are included in my tutorial).

white screen=better than black, so once you are there just find an older ati driiver that works

---

