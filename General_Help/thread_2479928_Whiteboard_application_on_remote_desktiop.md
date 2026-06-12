---
title: "Whiteboard application on remote desktiop"
date: 2022-10-13
forum: General Help
---

### Post by ODBWilson on 2022-10-13
Hi,

Is that possible using VNC to draw something on remote desktop, like whiteboard app?
Now I have a notice board application on lubuntu desktop, see if the user can access by VNC to draw something on it? 

Thanks,
Wilson

---

### Post by TheFu on 2022-10-13
VNC is really terrible security, so I wouldn't allow it without either a full VPN or ssh tunnel mandated - in VNC the way to force this is to allow only localhost connections to the VNC server.

But there is an easier, secure, 2-3x faster solution by using x2go or any NX-based remote desktop.

BTW, remote desktops are a hack and shouldn't be used on the same LAN, since using the built-in X/11 forwarding through ssh is faster, more convenient and much more flexible.  I'm constantly running programs on different LAN machines, but having the display window on my workstation. This is much easier and should "just work", since X/Windows has supported this mode for 40 yrs.

I really wish that VNC would just die already.  It is the worst of bad choices.  RDP isn't much better. the only reason it is still used is that MSFT pushes it and nobody looks too closely at interoperability of the security between different OSes, which is terrible.  For Windows-to-Windows, RDP is the best choice. Any other OS in the mix and it starts failing due to incompatible security.

Just use x2go. There are clients for Windows, OSX, Linux and it is very fast and flexible.  Multiple people can connect in read-only mode with 1 person driving.  Sorta like screen or tmux, but for remote desktops.  

To show people stuff - stuff that isn't classified or sensitive - we use a typical webrtc video conferencing tool called Jitsi Meet.  There are free servers for anyone to use or you can spin up your own if you have the bandwidth and connectivity for others to access in about 20 minutes the first time and 2-3 minutes after that.  Jitsi Meet allows sharing a single window or a full desktop.  meet.jit.si is the URL you can try it out.  To create a room, make up a name (don't use spaces) and share the URL with others.  No need to register.  No need to have the jisti meet tool create a room ..... a random URL in the correct format will automatically create a room as requested.  We do this to have family meetings.  The people used to Zoom get confused, but they figure it out quickly.

---

### Post by ODBWilson on 2022-10-14
Thank You for your advice.  I am not doing video conferencing.
I just need to write up text/draw someting on top of the notice board (that is an image).
Any recommended software to achieve this?

Thanks!

---

### Post by TheFu on 2022-10-14
> **ODBWilson said:**
> Thank You for your advice.  I am not doing video conferencing.
I just need to write up text/draw someting on top of the notice board (that is an image).
Any recommended software to achieve this?

Thanks!

Your question was whether VNC would work with a drawing application. Probably, it would depend on the application and whether the system is using Wayland or X/11.   x2go is a better remote desktop solution for many reasons.

For some reason, I thought you wanted multiple people to see the drawing or to allow someone remote to do the drawing inside VNC, while someone local watched.  VNC/x2go/rdp use "virtual desktops", so the local desktop wouldn't actually display anything for the local person to see.  This is different from the way that VNC works on _that other OS_. It is better in many ways and worse in 1.  OTOH, you may not have asked this and I jumped ahead to the only reason why a remote desktop would be used at all - in my world. Sorry.

If the question was about which drawing application to use, I don't know.  I use some that are for engineers to diagram stuff, but that's very different from what an artist would choose.  My application choices all work over x2go, however.

---

