---
title: "Broken desktop environment. Blank screen at login."
date: 2013-02-18
forum: General Help
---

### Post by 6xors on 2013-02-18
I just installed gnome and cinnamon one right after the other.

I rebooted my computer and when Ubuntu booted up I was greeted by a blank screen with a purple box with black borders. No login or password fields. No option to select the guest account and no wallpaper.

I am able to ctrl+alt+f1 and I am able to ctrl+alt+del. When I reboot I do see the animated Ubuntu logo.

These are the two desktops that I installed.

The first was "gnome shell" that I installed from the Ubuntu Software Center.

The second was Cinnamon that I installed from the terminal via three lines.

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```

I tried one fix which was to run > sudo dpkg-reconfigure lightdm but that didn't work. When I left the terminal the purple on the screen was now black with a black border of a different shade. On reboot the purple box with black border appeared.

---

