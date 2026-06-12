---
title: "Retroarch not detecting controller"
date: 2019-08-28
forum: General Help
---

### Post by ytterbious on 2019-08-28
I have an Xbox One controller I am trying to connect to Retroarch. It used to work very well in the past and for whatever reason has stopped. Thus far, nothing has helped. When I go to Settings > Input > User 1 Binds and try to to find the controller under "User 1 Device Index", nothing shows up. I have used the arrow keys to look for it, but it just stays "Disabled". So far, I have tried:

sudo snap connect retroarch:raw-usb
sudo snap connect retroarch:joystick

reinstalling Retroarch from every source I can (3 different versions in the software center, also tried Snap)

building from source (can't do it because I get a public key-related error for output after the command:
sudo add-apt-repository ppa:libretro/stable     )

tried changing the drivers (under Settings > Drivers) for input and joystick to every conceivable permutation

---

### Post by ytterbious on 2019-08-28
Wow. So it was connecting to my Steam Link I was trying to use earlier today. False alarm.

---

