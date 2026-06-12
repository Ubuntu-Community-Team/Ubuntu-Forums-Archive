---
title: "After Shutter freeze and reboot, Gnome tweak settings all changed...any idea why?"
date: 2018-06-27
forum: General Help
---

### Post by sometimescasey on 2018-06-27
On Ubuntu 16.04 using Gnome and gdm3.

I use [Shutter]("http://shutter-project.org/downloads/") for screenshots. Every once in a while, Shutter freezes. Usually I hit Alt+F2 and run xkill to kill it, and everything is fine again.

This time after hitting Alt-F2 and typing xkill the "x" cursor didn't appear. I blindly clicked around a bit to no avail, and then did a reboot with my power button.

Upon logging back into Ubuntu I discover that a bunch of settings have changed and I can't understand why:

- I use gnome-tweak-tool: my dash-to-dock shell extension and frippery-move-clock have been toggled off. My Ambiance theme looks weird and all the words in the menus are squished together with no spacing in between them.
- My terminal background color has changed from purple to black and the text is now gray
- My natural scrolling has been turned off
- I've been logged out of my Google account in Chrome

I tried uninstalling and reinstalling gnome-shell. Then tried uninstalling and reinstalling Gnome with lightdm. Everything still looks funny.

I get that these are all individually fixable changes but I'm a little alarmed that it's happened at all, because I don't understand what caused it. I've been using Ubuntu as my full-time OS for a few months now and don't mind when things get broken upon installing or uninstalling some package but in this case I'm a little weirded out that so many changes can happen to my OS upon a simple restart after Shutter freezes.

Can anyone who understands the inner workings of GNOME shed some light on what may have happened here? Thanks.

---

