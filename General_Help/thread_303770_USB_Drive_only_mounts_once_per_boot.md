---
title: "USB Drive only mounts once per boot"
date: 2006-11-20
forum: General Help
---

### Post by Monkey358 on 2006-11-20
Ok I have an 80GB Western Digital Passport portable USB hard drive here. Before I updated to Edgy it worked fine, but now whenever I connect it to my desktop it mounts fine, then if I eject/unplug it, I need to reboot before it'll work again. Drive works fine on other computers with no issues, so I know it's ok. Running tail -f on /var/log/messages shows a lot of "reset high speed USB device" and "Device not ready" messages, but only after its been unmounted, unplugged and replugged.

It's a royal pain to have to reboot to use it, so...help?

---

### Post by Monkey358 on 2006-11-20
I fixed it, I did some creative viewing of /var/log/messages, dmesg and lsmod and I figured out it seems that the uhci_hcd and ehci_hcd modules were both engaging when I connected it, but only ehci_hcd was disengaging on the eject, so I blacklisted uhci_hcd and now it works

---

