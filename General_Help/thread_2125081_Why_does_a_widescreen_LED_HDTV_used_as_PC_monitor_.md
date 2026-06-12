---
title: "Why does a widescreen LED HDTV used as PC monitor only show standard skinny width?"
date: 2013-03-12
forum: General Help
---

### Post by sdowney717 on 2013-03-12
This is my 78 yr old father in law's PC. It is Possible he messed up some setting but wont admit it.

I am baffled as it used to display the screen image in wide screen.
Now it displays only the old style width.

When it boots, the cursor is blinking about 2 inches in from the edge.
When the LED monitor detects no signal, It floats the screen resolution on the screen all the way to the edge as before, saying 1920 by whatever, wide screen resolution.

I also notice when the PC bios screen comes up it is not wide screen but dont know if that is relevant.

I tried uninstalling the Nvidia driver which made no difference.

Before I uninstalled Nvidia driver, the screen was shrunk so that the normally round clock was oval.
After the uninstall then also reinstall Nvidia driver, the clock was perfectly round. And the screen is still NOT wide screen.

---

### Post by SeijiSensei on 2013-03-13
What do you see if you run the NVIDIA X Server Settings application?  Does it detect the TV's EDID?  What resolutions are offered?  

After you reinstalled the driver did you run "sudo nvidia-xconfig"?

Perhaps you can try generating an xorg.conf file from the Server Settings app and editing the Modeline to add any missing resolutions?

Are you sure the TV is set to widescreen on the input connected to the PC?

---

### Post by sdowney717 on 2013-03-13
> Are you sure the TV is set to widescreen on the input connected to the PC?

Thanks, that I need to find out!

Perhaps he pushed some button on the remote that changed the aspect ratio?

---

### Post by tgalati4 on 2013-03-13
Most modern TV's have a P.Size button that changes the aspect ratio from 4:3 to 16:9 or "normal" to "stretch" or "zoom".  Find the remote and start pushing buttons.

---

