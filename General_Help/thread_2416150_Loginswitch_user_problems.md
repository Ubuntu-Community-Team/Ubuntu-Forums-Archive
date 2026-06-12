---
title: "Login/switch user problems"
date: 2019-04-05
forum: General Help
---

### Post by ruberad on 2019-04-05
So I've got a ThinkPad P50 laptop that I recently added Ubuntu 18.04 to. It was working fine for a week or so, I'm playing around with a lot of things. 

Since the 1920x1080 resolution on the 15" screen is pretty tiny, I gave a try to the Accessibility/Large Text setting. I didn't like it and changed it back, but now all my resoultions are jacked up. Now Settings/Devices/Displays only lets me choose between 920x540 and 864x486.

Googling got me as far as putting a couple xrandr commands in a ~/.xconfig file, which gets things back to 1920x1080 for my account, but the login screen is still big and fat, and the same .xconfig file does not work for my wife's account.

I can boot up, and use the fat-rez login screen to log into either account, but if I then try to switch accounts, or log out to log into another account, the login screen is just the bionic beaver background image, no login tiles, and the keyboard and mouse are completely inactive, forcing me to power-cycle to reboot.

I've tried putting into /etc/grub/default
GRUB_GFXMODE=1920x1080
GRUB_GFXPAYLOAD_LINUX=keep
and grub-update, no joy.

I've tried copying ~/.config/monitors.xml (which looks good with 1920x1080) into /var/lib/gdm3/.config/, no joy

(a) why did switching to large text blow away all the available screen resolutions that used to be available in settings/devices/displays/resolution?

(b) why does the original login screen work (although with fat resolution), but logging out or switching user doesn't?

(c) how can I fix this?

thx in advance!

---

