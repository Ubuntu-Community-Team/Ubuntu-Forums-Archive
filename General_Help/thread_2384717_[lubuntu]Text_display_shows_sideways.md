---
title: "[lubuntu]Text display shows sideways"
date: 2018-02-11
forum: General Help
---

### Post by karel2 on 2018-02-11
I just installed Lubuntu on an ASUS T101HA-GR004T. This took some fiddling because of the Atom hardware platform; isorespin.sh helped me out - gratitude and kudos to linuxium!

Now I have a bootable Lubuntu 17.10, with one major inconvenience: the display is rotated by 90 degrees. Mind you, this is NOT about the X-system so please do not tell me about xrandr, I know that one. But the issue is deeper, at least one layer below X: the text screens, accessed with ctl-alt-[f1:f6] (which I often use!) are also on their side. Could it be a setting in grub.conf?

PS @mods: apologies if posted in incorrect section, feel free to move.

---

### Post by wildmanne39 on 2018-02-11
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by mörgæs on 2018-02-11
Here is a description of another problem for Atom processors. Though it's not the same problem as yours the solution in the last post is still worth a try.

[https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

---

### Post by karel2 on 2018-02-15
My apologies for not coming back any sooner - influenza time down here.
As per the suggestion, I added to /etc/default/grub the line
GRUB_GFXPAYLOAD_LINUX=text
then regenerated the real grub configuration with
update-grub

Regretfully that changes nothing, the text and graphical screens are still standing "on their side".
I tried activating the GRUB_GFXMODE=640x480 that is commented out in /etc/default/grub with equal lack of success.

Meanwhile, I also booted from a USB stick with a stock Ubuntu 16.10 : still the same effect.

Any tips or recommendations, please?

---

### Post by mörgæs on 2018-02-15
Since it's very new hardware I suggest that you try 18.04 though it's not formally released yet.

---

### Post by karel2 on 2018-02-27
Downloaded  18.04 today, copied to USB stick and booted from that. Same behaviour  as before, the display is rotated by 90 degrees. HELP!

---

### Post by kerry_s on 2018-02-27
yeah, you should grab normal ubuntu or gnome, it's made to support tablet things and has a rotation lock at the bottom of the indicator menu. (the icon to the right of settings)

other *buntu's are made for a different purpose, run lighter on older hardware, more customize-able, etc....

---

### Post by karel2 on 2018-02-27
My previous message was not complete: I installed the 18.04 and it does detect rotation - when I rotate the device, the display will tilt 90 degrees too. Great, now I have something workable. Still things are not perfect: the text consoles, available through alt-f1 - alt-f6 are still on their side, as is the grub boot menu. Worse: from the text consoles I find myself unable to return to the graphical desktop with the usual alt-f7. And, again, I quite rely on those text consoles, having learned Unix before the days of GUIs :)

---

### Post by kerry_s on 2018-02-27
lol, yeah modern hardware sure is a hassle. who wants to use a full screen terminal over a gui, thats just crazy.

learning never stops, adaption is the key to peace of mind.

---

### Post by HermanAB on 2018-02-27
It sure sounds like a pain in the neck...

---

### Post by mörgæs on 2018-02-27
If 18.04 is the best release yet for your hardware I suggest that you discuss the problem in the [development forum]("https://ubuntuforums.org/forumdisplay.php?f=427"). If needed then people there can help you create a bug report.

---

### Post by karel2 on 2018-03-10
Installed 18.04 now, which is apparently a work in progress - as expected.
On the good side: physicalluy rotating the screen is detected by hardware and the display gets tilted accordingly. Which means my graphical screens are useable now. Well done!
Less good: I still can switch to the text console with alt-ctl-f[1-6] - but I still can't switch back to the graphical desktop with Ctl-(alt)-F7.
And, as before, the initial boot, including the grub menu, AND all text consoles, are still on their side.

Deveopers are welcome to incur my assistance for testing/validating.

---

### Post by mörgæs on 2018-03-10
> **karel2 said:**
> 
Developers are welcome to incur my assistance for testing/validating.

Thanks for that. As mentioned above you need to present your problem in the development forum so people there can judge if and how to open a bug report.

---

### Post by karel2 on 2018-03-10
Sorry, @morgaes, I am available for assistance, and I have told my story. I am not going to tell it again. And perhaps you do not mean it like that but I do not like being told what to do when I offer my help.

---

### Post by QIII on 2018-03-10
Nonetheless, any discussion/support regarding 18.04 belongs in the Development Version sub-forum.

Not that the Canonical developers will see your gracious offer there in any case, since they don't hang out on the Ubuntu Forums.

Closed.

---

