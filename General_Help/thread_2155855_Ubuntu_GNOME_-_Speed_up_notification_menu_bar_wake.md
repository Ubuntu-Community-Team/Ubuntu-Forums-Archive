---
title: "Ubuntu GNOME - Speed up notification menu bar wake up time?"
date: 2013-06-19
forum: General Help
---

### Post by Roasted on 2013-06-19
I'm running Ubuntu GNOME 13.04 64 bit with the Gnome3 PPA, which brought my Gnome version to 3.8.2. If you hold your cursor at the bottom of the screen, the notification bar will show up. Likewise, you can hit SUPER + M to bring it up. I'm curious if there's a way to speed up the reveal time so if I put my mouse at the bottom of the screen, it comes up much quicker. Any ideas?

Thanks!

EDIT - Cancel that. It's in the Staging PPA.

EDIT II - Where on earth is the mark as solved tool now?

---

### Post by markbl on 2013-06-19
I don't use the staging PPA but I don't understand how that can fix this? Gnome-shell requires xorg 1.14 to enable the new "pressure sensitive" message tray. We are just currently seeing the crappy fallback implementation currently in Ubuntu 13.04 which uses xorg 1.13.

---

### Post by Roasted on 2013-06-19
I think I edited the wrong thread. I posted two threads with different questions about Gnome Shell. Originally I wasn't able to find the privacy and search functions in system settings, but they were part of the staging PPA. This thread I was asking about the time to wake up the message tray. My mistake!

Good to know about the pressure sensitivity feature coming in 13.10, though. I still wish something was adjustable in 13.04... that makes it kind of obnoxious. :(

---

### Post by Roasted on 2013-06-20
A user in the Gnome IRC channel helped me out. I had to do the following:

sudo gedit /usr/share/gnome-shell/js/ui/messageTray.js

Search for TRAY_DWELL_TIME.

By default on my system, it was set to 1000ms. I set it to 200ms and it feels a lot more comfortable to me. This should serve as a decent alternative until 13.10 lands with xorg 1.14, providing Gnome users with a pressure sensitive message tray.

---

### Post by cincinnatus13 on 2013-06-20
Thanks, gonna edit mine. That's one thing I hadn't figured out either but just left it as I don't use it all that much.

---

### Post by Roasted on 2013-06-20
> **cincinnatus13 said:**
> Thanks, gonna edit mine. That's one thing I hadn't figured out either but just left it as I don't use it all that much.

I find it's default setting is rather obnoxious. I am anxious about the 13.10 Ubuntu GNOME due to xorg 1.14 and the pressure sensitivity. My buddy is on Arch and did a screencast of his... looks very handy. For the time being, I find this to be an extremely acceptable workaround. :guitar:

---

