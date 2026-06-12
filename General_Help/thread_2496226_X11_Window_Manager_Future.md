---
title: "X11 Window Manager Future"
date: 2024-03-19
forum: General Help
---

### Post by speartip on 2024-03-19
Does anyone know if X11 is going to be included as an alternative in 24.04?
The reason I ask is that I still find X11 a far smoother and snappier experience than Wayland.

---

### Post by ajgreeny on 2024-03-19
I'm pretty sure it is still included in Noble-24.04 though for the standard Ubuntu system I think wayland is the default. 
I steer away from anything to do with gnome so I haven't even tried Ubuntu 24.04 as I do just about all the other versions of Noble some of which don't yet offer wayland as an option at login.

I don't think you need to worry just yet, though in future, who knows!

---

### Post by speartip on 2024-03-19
Thanks Ajgreeny. I'm pleased about that. Wayland may well have improved in 24.04 so I may go with it on my Intel based system, but for now Wayland just feels a bit clunky compared to X11.

---

### Post by MAFoElffen on 2024-03-19
Ubuntu Noble 24.04 still has X11.

X11 is not going away soon. Even though people talk about it from time to time. Wayland is an alternative to X11, but still not a full replacement. There are still many things that can only be done with X11, that Wayland does not do. For example, X-Forwarding for running applications from remote computers, screen recording, and screen casting. Wayland’s minimal core protocols are lacking most of the features that  non-trivial apps and desktops actually need to work–such as screen  locking, screen sharing, cross-app window activation, non-integer  scaling, and so on. 

Another is running GUI X applications for Windows WSLg. ... But that is rather using "Weston" as the main compositor for Wayland... And is not straight forward to install and configure on that platform.  

Next is how the native installed application are written to display. There are not a lot of Native Wayland applications. Most applications are still written to default display from X11. Most people do not realize that an application that is not written to display natively as Wayland runs through XWayland, which allows those legacy applications to still run on top of Xorg server, but display in a Wayland session. <-- _So uses both Graphics Engines_.

Yes. It is still a thing that is being worked on... That started and is still being developed by X Dev's.

---

### Post by speartip on 2024-03-21
Thank you for your explanation

---

