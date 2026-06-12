---
title: "Best RDP (or the alike) for MacOS (Catalina+) -&gt; Ubuntu Desktop?"
date: 2020-01-14
forum: General Help
---

### Post by guice on 2020-01-14
Okay, I'm now resorting to the forums. I'm trying to find a good, functioning, RDP setup to connect to my Ubuntu box. I have it installed and running on a mini-PC for months. It does NOT have a monitor connected (after I installed Ubuntu Desktop, I removed the monitor).

I've been looking at options, none of them seem to work or be efficient:

* x2go doesn't work on Catalina.
* vino is not compatible with Catalina's VNC client.
* TigerVNC is slow redraw rate - I'm literally on a LAN connection with the mini-box.

What are the other options? I'm surprised these things seem to be so hard to get working.

Thanks,

---

### Post by TheFu on 2020-01-14
Normal remote-X11?  Do Macs support that?

---

### Post by guice on 2020-01-14
x2go is X11. It's not working very well. I couldn't get anything to show. I got a flashed X11 window like something was happening, then disappeared. Nothing.

---

### Post by TheFu on 2020-01-14
No, x2go uses the NX protocol.  x2go has issues with the default Ubuntu Gnome3 GUI, so most people use a different DE, like XFCE, LXDE, or Mate when using x2go.

X11 uses X11.  I know Unix-savvy OSX people will setup an X11 server on their Macs so they can run X11 clients from remote systems.

---

### Post by HermanAB on 2020-01-15
Install HomeBrew on the Mac.  Then install an X server on both Mac and Ubuntu.  After that, you can use SSH with X forwarding between them.

---

