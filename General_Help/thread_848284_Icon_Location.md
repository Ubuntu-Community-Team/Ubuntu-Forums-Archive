---
title: "Icon Location"
date: 2008-07-03
forum: General Help
---

### Post by tuxxy on 2008-07-03
Hi,

I have changed most of my icons on the Main Menu and taskbar area, however when I load up an application for example Firefox or Open Office, the icon presented in the top left corner of the application are the older versions of the icons and not the ones I updated to which seems weird, as they are correct for launching the application, any idea where these small icons are located so I can edit them?

at the moment I am just gettin a blank application icon for OpenOffice and the older firefox icons in browser but for anything else thye are working with the new ones which puzzles me...

thanks

tux

---

### Post by tuxxy on 2008-07-03
Here I have an image to help show which icons these are, as I still have not found them...

---

### Post by tuxxy on 2008-07-03
bump?

---

### Post by Plasma_NZ on 2008-07-04
I dont know where firefox icons are located.. but i do know where alot are located..

/usr/share/app-install/icons

As for changing a programs icon in the top-left, im not entirely sure u can.. as that is probley coded into the application..

---

### Post by tuxxy on 2008-07-08
Hi,

I solved this problem with help from IRC, it was to do with the gnome-utilities icon being at fault and affecting all terminal icons because of this.  As for Firefox I was told that non gnome apps are not always the same.

I am having the exact same problem now in OpenOffice, everytime I run an OO application it will display the horrible white application box again instead of the nice OO icons I have.  The icons I use to run the application are fine and the main menu icons are all fine its just when I run the applications.

I have narrowed it down to the /usr/share/icons/gnome/24x24/apps folder, from what I can see these icons should be being used when I run any OO app, however they are not displayed does anyone have a clue why?

tux

---

### Post by tuxxy on 2008-07-08
Solved!

Re-install of OpenOffice Fixed it, looks weird now as before my Openoofice toolbars were all text only and now all Icon only so there was definitely something goin wrong!

---

