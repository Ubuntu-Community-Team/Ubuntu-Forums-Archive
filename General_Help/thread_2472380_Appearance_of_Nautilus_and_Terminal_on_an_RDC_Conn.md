---
title: "Appearance of Nautilus and Terminal on an RDC Connection"
date: 2022-02-25
forum: General Help
---

### Post by taholmes160 on 2022-02-25
[COLOR=#232629][FONT=-apple-system]Hi Folks: When I first set up my ubuntu system, and was using the local screen, keyboard and mouse, the terminal window and nautilus both had really good looking themes on them. The machine is intended to run headless over the local area network and is accessed via RDC -- for some reason, the themes have vanished when I connect via RDC and the current ones are really ugly -- anyone know how I can fix this?

[/FONT][/COLOR][IMG]https://cdn.discordapp.com/attachments/946580367052255252/946580476007686164/unknown.png[/IMG]

---

### Post by TheFu on 2022-02-26
What is RDC?

Gnome breaks many remote access tools or makes them perform very, very, badly.  Use a different DE and use something like **x2go** for the best performance. Avoid RDP and VNC-based solutions. Everyone who changes to x2go (NX protocol solution) says it is like day when compared to the night of both VNC or RDP.

x2go how-to: [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)

If your client system runs X/Windows, there are even better, fully integrated, solutions. It is better NOT to use a full remote desktop when that just isn't necessary.  I run applications constantly on other systems than the one I'm sitting behind using remote X11. Each of those windows integrates with my local desktop where I can't tell the difference between local and remote windows. Performance is excellent, but that is dependent on the LAN networking. My network is 100% wired, GigE ethernet. As long as you have at least 100Mbps, it would feel like local, native, performance. Wifi can be a problem, but wifi is almost always a problem when a stable connection is necessary, regardless of protocol.

Try x2go. You won't be disappointed, provided you leave Gnome3+ behind.

---

### Post by MAFoElffen on 2022-02-26
> **TheFu said:**
> What is RDC?

His picture posted looks to me as a screenshot of the current window of a Remote Desktop Protocol (RDP) session from a Windows OS to his Ubuntu Session running remotely on that address.

So I believe the OP meant he is using "RDP", running from Windows.

---

