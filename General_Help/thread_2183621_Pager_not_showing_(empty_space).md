---
title: "Pager not showing (empty space)"
date: 2013-10-25
forum: General Help
---

### Post by sbottorf on 2013-10-25
I've installed Lubuntu 13.10 and like it but the pager sometimes disappears on the bottom panel. If I open and close windows on the desktops the panel will sometimes come back but it quickly disappears again. I can click in the emppty space and change desktops but it is like working blind. I believe I have the default OpenBox and desktop settings. I've tried changing some items but still no reliable pager. I did not notice this problem in Lubuntu 13.04 on the same hardware.

Any ideas? 

Stew Bottorf

---

### Post by sbottorf on 2013-10-25
Just to suggest a workaround for this problem: 

in Panel Preferences/ Appearance, select "Solid Color" or "Image" but then use "background.png" (not lbuntu-background.png). This makes the background of the whole bottom panel dark or black. Then to read clock adjust the font color to white. 

This is not pretty but it seems to work better for the pager. So far nothing has disappeared. Maybe there is a better way?

---

### Post by Dennis N on 2013-10-25
I use Lubuntu, but have not yet installed 13.10 (not yet sure I will). I loaded up the live 13.10 cd and I see the problem. When the mouse cursor tooltip covers the pager windows, and then is moved away, the background in the pager windows reappears in the panel color, making the whole pager invisible. Definitely a little bug. It is not restored until you open a window. You seem to have found a solution, but I will play around with it a bit more.

Also found:

Desktop Pager Settings dialog does not appear when right-clicking on the pager and selecting it, so I cannot change the number of desktops here.

Update on these problems for interested readers:

One day later, I used the same install media on a newer desktop machine and the pager visibility problem was NOT present. But the problem with the desktop pager settings dialog not appearing was still present. So the first problem may appear only on some systems. Solutions I used are in posts 4 and 5.

---

### Post by Dennis N on 2013-10-25
**A solution with a gray panel (or any panel color of your choice):**

Panel Settings > Panel Preferences > Appearance > Background > Mark "Solid color (with opacity)" > Click on the little rectangle just to the right of "Solid color (with opacity)" - Choose a shade of gray to your liking; or use the little eyedropper to match the panel color. Choose opacity (0 = transparent, 255 = opaque) - Click OK

After doing this, the tooltip no longer messes up the pager. Fixed.

(The Desktop Pager Settings dialog is not fixed, however. Edit: See post #5 for solution to this.).

---

### Post by Dennis N on 2013-10-25
[B]Fix for "Desktop Pager Settings" Dialog not appearing when selected:
[/B]
Main Menu > Openbox Configuration Manager > Desktops Tab > Select number of desktops wanted in the "Number of desktops" selector window.

Close the Dialog. All is good.

---

### Post by walterorlin on 2013-10-26
Or alternative you can launch that from the terminal by the obconf command

---

### Post by gruen64 on 2013-10-26
> **sbottorf said:**
> I've installed Lubuntu 13.10 and like it but  the pager sometimes disappears on the bottom panel. If I open and close  windows on the desktops the panel will sometimes come back but it  quickly disappears again. I can click in the emppty space and change  desktops but it is like working blind. I believe I have the default  OpenBox and desktop settings. I've tried changing some items but still  no reliable pager. I did not notice this problem in Lubuntu 13.04 on the  same hardware.

Same problem here with my upgraded installation. Did you upgrade from the previous version or did you make a clean install?

---

### Post by gruen64 on 2013-10-26
Sorry, double posting. :-/

---

