---
title: "XGL-Hardy-ATI 8.4"
date: 2008-05-01
forum: General Help
---

### Post by awatts on 2008-05-01
So i have an ASUS f3ka w/ ati radeon 2600hd.  Its running aiglx right now but all my opengl apps flicker really bad.  I know this is a problem with the 8.4 driver.  On my old laptop with the old drivers (which do not work for my current card) i used xgl and the nonXGL trick to run my apps.  so far as i know there is no good way to run these programs in aiglx without compiz (short of disabling it causing me to loose my settings.)  Is it possible to use the 8.4 driver with xgl rather than aiglx? and if so how do i go about it?

---

### Post by Killerah on 2008-05-03
I'm in the same boat, all my openGL apps have this black flickering thing, if there's no fix for it in aiglx I'd rather go back to XGL (though I hope I don't have to).

---

### Post by esteckis on 2008-05-03
Per the ATI wiki, you have to switch to non on the visual effects. That solved my black flickering screen with any opnegl screen saver and stopped Google Earth from crashing.  Now if you want to be able to switch compiz fusion on or off easily, go to synaptics package manager and download the fusion-icon to put an icon in the tray to enable or disable compiz fusion. I downloaded it, but since I am a newbie, I am trying to find it now, lol.

OK, I found it, synaptic put the icon under the systems tools menu.
**NEW IMPORTANT NOTE**:
I thought I was able to fix it and enable visual effects, I was wrong. If you use the icon, you can have compiz run but no opengl, if you use the matacity window manager you can run programs using OpenGl but that brings appearence- visual effects down to "none".

---

### Post by awatts on 2008-05-08
Yes it all works with no Compiz. 

Since there is no AIGLX workaround, what about rolling back to XGL? can this be done with my card (Radeon Mobility 2600hd) and the new drivers?
[B]
Another thought:[/B] You know how in windows you can select the option to run a program without desktop effects enabled...there really should be a way to fix this problem like that in Ubuntu, at least for full screen apps like ppracer.  Is there anyway to make a launcher or command that will turn Compiz/AIGLX off as/before it launches the program?  It would also be good to find a way to automatically start Compiz again when the program is closed.  I'm sure someone could make this happen, just not me :)

---

### Post by nic-stange on 2008-05-24
Hi, 
i got the same flickering running OpenGl apps.
Using fusion-icon and swithicng window-manager from 'Compiz' to 'Metacity' imediately solves the problem.
Deactivating all Compiz-Effects doesn't work for me. Maybe it's some general option?

Regards

Nicolai

---

