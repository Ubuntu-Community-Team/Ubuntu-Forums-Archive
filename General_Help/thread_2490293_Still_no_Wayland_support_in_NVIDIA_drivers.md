---
title: "Still no Wayland support in NVIDIA drivers?"
date: 2023-08-29
forum: General Help
---

### Post by flix3 on 2023-08-29
Hello,

On my Ubuntu 22.04.3 LTS I've just installed the "proprietary and tested" NVIDIA driver (version 535.86.05) from "Software & Updates/Additional Driver". [see attached image 1]

So far, so good. But now when I log in in a Wayland session, I see in "Settings/About": [see attached image 2] Graphics: llvmpipe (LLVM 15.0.7, 256 bits); Windowing System: Wayland.

Whereas when I log in in an X11 session I get: [see attached image 3] Graphics: NVIDIA Corporation TU117 [GeForce GTX 1650]; Windowing System: X11.

As you can see the default drivers in Wayland are from Mesa (AFAIK).
Is it possible to use the NVIDIA driver with Wayland?

Thank you in advance for your help.

[Edit:] I've seen that the attached images are available for logged-in users only, so I've added additional details to my post.


[**SOLVED**] I've solved this myself. All I've done was to install **libnvidia-egl-wayland1**, and reboot. Now "Settings/About" shows me: Graphics: NVIDIA GeForce GTX 1650/PCIe/SSE2; Windowing System: Wayland.
I wonder why that library is not installed by default with the NVIDIA driver...

---

### Post by TheFu on 2023-08-29
Maybe this is a question for nvidia?  After all, it is their drivers.

---

### Post by flix3 on 2023-08-29
Thank you, but I've (hopefully) solved it by myself.

---

