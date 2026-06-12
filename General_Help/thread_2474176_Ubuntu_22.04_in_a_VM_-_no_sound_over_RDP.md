---
title: "Ubuntu 22.04 in a VM - no sound over RDP"
date: 2022-04-23
forum: General Help
---

### Post by hgpuke2 on 2022-04-23
Hi! I've just installed Ubuntu 22.04 in a VM on my Proxmox server (internally using KVM/QEMU virtualization).
As Ubuntu 22.04 is now using Wayland rather than X11 and RDP rather than VNC, it is quite different to 20.04 from a remote desktop perspective.
I've turned on Remote Desktop sharing and control in the control panel.
I remote into it from a computer running Windows 10 and Windows Remote Desktop software as part of the standard Win10 Pro install.
Video performance is excellent - much better than in 20.04 running X11 and xrdp. However, I get no sound at all.
Looking in the control panel of Ubuntu 22.04 I only find a "Dummy output", which obviously is not going to work.
In 20.04 I had to type in "pulseaudio -k" in the terminal to get sound working. This would get me a new device in the control panel for sound.
Doing the same in 22.04 has no effect, I am guessing that Wayland treats this differently.

Is there a way to get sound working when using Ubuntu 22.04 as a Virtual Machine (using KVM/QEMU) at all? Together with the new RDP-based Remote Desktop Sharing of Gnome 42 using Wayland?

Thanks for any support.

---

