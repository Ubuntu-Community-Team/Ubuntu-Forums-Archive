---
title: "ProtonVPN no longer showing up on applications menu"
date: 2024-01-12
forum: General Help
---

### Post by wannabe-programmer on 2024-01-12
I've used Proton VPN in the past, but now it's suddenly not listed under my programs menu / application launcher.
I'm pretty sure it's still installed because I see it updating when I'm doing updates.

I also tried:
```
sudo apt list --installed | grep proton
```
and it responded:
protonvpn-stable-release/unknown,now 1.0.3-2 all [installed]

I also tried: ```
dpkg --list | grep proton
```
and it returned protonvpn-stable-release

So I think it's still installed, I just don't see the icon.

I was thinking I could start it from the terminal but it didn't work when I typed:
"protonvpn" or "protonvpn-stable-release".
It said "command not found."

Is there a way to refresh the app launcher so it will show the ProtonVPN icon again?

I'm using Ubuntu 20.04

Any input is appreciated.

---

