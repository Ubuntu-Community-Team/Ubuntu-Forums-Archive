---
title: "Getting Awesome WM to work while keeping Gnome utilities"
date: 2022-06-11
forum: General Help
---

### Post by dpl-dpl on 2022-06-11
Hi, 

I want to use Awesome WM while still keeping Gnome utilities.

What I tried so far: there are quite some threads on this online, however rather outdated:
e.g., [https://edwardtremel.com/awesome.html](https://edwardtremel.com/awesome.html) , [https://scaron.info/blog/awesome-with-gnome-on-ubuntu.html](https://scaron.info/blog/awesome-with-gnome-on-ubuntu.html) , etc., however following these do not even allow me to launch into a working session (error message right after user login screen asking me to log out again).

The least-outdated, or at least somehow working, of these seems to be the Arch Linux AUR PKGBuild for their Awesome-gnome package: [https://aur.archlinux.org/packages/awesome-gnome](https://aur.archlinux.org/packages/awesome-gnome) . So I copied the content of the three files contained there, which at least allows me to launch a session, but didn't make the Gnome integration work. So in addition, I followed the sed commands for /usr/share/applications/gnome-control-center.desktop , /usr/share/applications/gnome-*-panel.desktop , and /etc/xdg/autostart/org.gnome.SettingsDaemon.*.desktop from [https://edwardtremel.com/awesome.html](https://edwardtremel.com/awesome.html), i.e., I modified all OnlyShowIn=GNOME;Unity; to OnlyShowIn=GNOME;Unity;Awesome GNOME;Awesome; (where in addition I used two different Awesome names, because the different tutorials out there seem to share the same config file contents, but disagree on what name to use they imply here).

Yet still, I lack the basic comfort of the regular Gnome environment and the gnome-control-center: second display/monitor is not recognized, custom shortcuts do not work, etc.

Does anyone have up-to-date recommendations? Thank you in advance!

Edit: All on a fresh, clean install of 22.04 done tonight, and fresh awesome install as well.

---

