---
title: "How? Remote control the display of a laptop server to show dedicated X-apps/dashboard"
date: 2013-05-24
forum: General Help
---

### Post by Tjalk on 2013-05-24
Hi there,

tried for hours to find the right keywords to search for pointers, but cannot seem to find the right search results, even though I used Unix/Linux off and on since '96 and searched this forum.

I have a laptop which functions as server for apache2/asterisk/domotica/logging/fileserver, which hosts various websites, but in the physical universe basically keeps my desk occupied.
It has 12.04LTS, X/Gnome.

I'd like to use remote commands (either through ssh or by programmatically from other machine (like Raspi)) to achieve the following:
[dream mode on]:
- control the laptop display to switch cycle between tty's (for top and tail log's) or any active X session
- multiple X-sessions without window-manager GUI FUNCTIONALITY (startbuttons/apps/taskbar/etc), or 1 session which can be controlled to display different area's of an virtual desktop-canvas.
- display an dedicated dashboard-like application to visualize current website usage and stats (perhaps a geo-map with reverse-ip lookups when logging http-requests)
- start a dedicated full screen app for teleconferencing (using it's webcam and the x-app fullscreen) and connect to a call
- show to-do items through an x-app
- perhaps add another smaller touchscreenlcd through the external vga and usb to function as a configurable user interface (graphical button's to control stuff); but this functionality could also be offloaded to another machine, like a raspberry with which I could add another custom keyboard); still any pointers to this are welcome! 


The idea is to start with command line for R&D , but to involve another machine to script real-world events and responses.

What I'm NOT looking for is, but keeps popping up in results are:
- X11-tunnel through Putty; the local laptop screen has to respond to commands from SSH/RPC(?)
- vnc to duplicate remote desktop: I do not want any desktop
- Kiosk mode (as in ruggedized public machine), I do not want to use it's keyboard or a windowmanager with direct input
- multi-seat
- presentation mode (as in consultant-style dual screen)

What keywords am I looking for;
- rpc? no experience
- x11?

Please advice on where to look with which technology and/or topic/keywords.

Best regards,
Tjalk

---

### Post by bnjmn2 on 2013-09-01
Hello World. (first time posting to forums).

Any progress / solutions for this? I'm in a very similar situation and, I agree, google results are quite fruitless; lots of stuff on X-window forwarding to my client. I want to remotely control the server devices (specifically the display via the network; over SSH would be great). Can't seem to find anything. 

Any ideas?

---

