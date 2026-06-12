---
title: "Random system lockups and screen freezes, hardware detection mishaps"
date: 2024-05-27
forum: General Help
---

### Post by sjodenzack on 2024-05-27
Good morning,

After a *long *hiatus I've come back to using Linux on my laptop. I'm getting back into web-dev and game occasionally. It generally acts as a desktop with two 32" Acer monitors running vertically on each side of it. I'm using a two USB hub(USB-C from Anker, USB-A from j5create) "USB-C dock" that I've made to hook up all my peripherals to switch between this and my Windows based work laptop with one cable. Everything runs through this one USB-C connection except for power, which uses a barrel style charger. No power is supplied through the hub/dock setup.

The laptop and maybe some relevant specs: Asus ROG ZEPHYRUS (model: GA401I)
[LIST]
[*]CPU is a Ryzen 7 400 series, 8 cores, 2.9 GHz
[*]GPU is an NVIDEA GeForce GTX 1650
[*]RAM: 24GB(Upgraded with Crucial RAM from factory installed of 8GB)
[*]NVMe SSD: 512 GB
[/LIST]

The main issue I'm running into is that sometimes when I return to my computer after some time away, one screen will be frozen. It may show the cursor, while the real cursor moves around on the other 2 screens. This could be any of the three screens, but generally is one of the Acers. Sometimes I can't move the cursor at all. Occasionally this happens while using the laptop the as well. Sometimes I can do a soft restart via the menu, often though it requires the hard shutdown with the power button.

Also, on rarer occasions, the audio devices will sometimes not appear on login, requiring a soft restart.

Some of the software I generally have loaded:

[LIST]
[*]Spotify
[*]Dropbox
[*]Steam
[*]CS2
[*]Visual Studio Code
[*]Signal
[*]Discord
[*]KVM with Virt-Manager
[/LIST]

I'm running kde-plasma-desktop with kde-baseapps as my DE/WM, and LightDM for my login screen. I don't have anything installed from source/compiled manually. I only use the official repos or the official .deb packages from those software providers which add their own repos for updates. The one piece of non opensource software I run is the proprietary driver for the NVIDIA video card so I can run CS2 properly, which I get through the software manager, also not built from source. 

This issue has occurred on the latest version of 22.04.XX LTS, and is now still occurring on the latest version of 24.04 LTS. (Both were/are fresh installs via .iso/USB sticks.)

If I could get any assistance in troubleshooting these issues, that would be great. I'm not sure which logs to look at, or even where/what the proper logs will/would be for these issues. I'm wondering if it's thermal related sometimes, as it does happen occasionally while running CS2 and my laptop will get hot. It's elevated and on a cooling fan pad, but still runs a bit hot. It's been a while since I've used Linux as a daily driver and I'm a little rusty. I used to run Arch and was semi-familiar with where things lived there, but I got tired of the maintenance and trusting the AUR and ended up just switching back to Windows for the light personal computing I did at the time.

---

### Post by currentshaft on 2024-05-27
For the frozen screen issue, you can try using Control+Alt+F1 through F7 to log in at a non-graphical console, check logs (I'd start with "sudo dmesg" and "/var/log/syslog"), and also kill stuck X sessions. You could also try a different window manager.

---

### Post by sjodenzack on 2024-05-27
Thank you for the tips on where to look. I will do that. As far as window managers go. I do like some of how KDE and Plasma work, but I'm not tied to anything. I'd probably try something like Openbox with tint2 or something like I used to use in Arch, it's just been so long. I'm really not a fan of Gnome and how it functions/looks.

---

