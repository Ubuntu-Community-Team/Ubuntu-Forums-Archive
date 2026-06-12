---
title: "Swapping monitor positions for guest session"
date: 2016-05-10
forum: General Help
---

### Post by antar on 2016-05-10
I have two monitors, each plugged into a separate graphics card. I'm using the nouveau driver.

Logged in under my own account, both monitors are detected, and I can reorder them in any way I see fit using the "displays" settings pane, and that configuration persists even after rebooting.

However, when I start a guest session, it always has the order of the monitors reversed (the right monitor on the left and vice versa). I can reorder them in the "displays" settings pane or using xrandr. However, if I log out and log back in, I'm back to the monitors being in the wrong order (which makes sense, since it's the guest session). So I'm wondering if there's somewhere I can change the settings to put the monitors in the correct configuration permanently.

I've already tried running xrandr as part of the guest session startup script. I've edited /etc/guest-session/prefs.sh and added:

```

echo "xrandr --addmode HDMI3 1920x1080" >> $HOME/.profile
echo "xrandr --auto --output VGA2 --left-of HDMI3" >> $HOME/.profile

```

but it appears this runs BEFORE whatever part of the session startup sets the displays, because while the monitors START in the right order, after about a second they switch back.

Any help is greatly appreciated. Thanks in advance!

---

