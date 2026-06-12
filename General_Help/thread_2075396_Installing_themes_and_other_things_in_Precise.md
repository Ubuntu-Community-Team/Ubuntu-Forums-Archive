---
title: "Installing themes and other things in Precise"
date: 2012-10-23
forum: General Help
---

### Post by oxf on 2012-10-23
Hi,

I'm running Precise and installed Gnome classic because I hated unity.
I then downloaded some additional Gnome themes via Synaptic but they don't show up in system settings>appearance. How do I find them?

Then the other thing thats bugging me is this. I put some quick links on the top panel but they are crammed all the way to the left. With previous releases if you right clicked on the icon you could move them andthen lock them. This is no longer an option in Precise.

Thanks for any help
Veronica

---

### Post by Frogs Hair on 2012-10-23
The appearance application that came with Gnome 2 was scraped by  Gnome . 

install Downloaded Themes or icons in 11.10-12.04-12.10

Install the Gnome Tweak Tool / Advanced Settings for making theme selections from the software center .  


Use only GTK 3.4 themes for 12.04 amd 3.2 themes for 11.10. Check this in the theme description at the download location. (3.6 themes for 12.10)

Download and fully extract the theme packages and hold the folders on the desktop until needed . 


(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.

(All Users) Use gksudo nautilus in the terminal to open  Nautilus as root and navigate to > File System / usr / share / themes or icons .

Place the folders in either Location . Use Advanced Settings to make theme selections . Logout - in may be required before themes are visible in Advanced Settings .

Edit: Use Alt + right click or super key + Alt right click to access panel properties. ( Classic Gnome / Fall Back  only)

---

### Post by oxf on 2012-10-25
> **Frogs Hair said:**
> The appearance application that came with Gnome 2 was scraped by  Gnome . 

install Downloaded Themes or icons in 11.10-12.04-12.10

Install the Gnome Tweak Tool / Advanced Settings for making theme selections from the software center .  


Use only GTK 3.4 themes for 12.04 amd 3.2 themes for 11.10. Check this in the theme description at the download location. (3.6 themes for 12.10)

Download and fully extract the theme packages and hold the folders on the desktop until needed . 




Thanks for the detailed instructions!

Does anyone know how to move the icon in the top panel?

---

