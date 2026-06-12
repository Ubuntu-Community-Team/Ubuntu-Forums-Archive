---
title: "Hostname changed to &quot;macaroni&quot;!"
date: 2004-10-30
forum: General Help
---

### Post by gmilldrum on 2004-10-30
Loaded up the Live CD, booted my ThinkPad T23 with no problems.   Looking at the default desktop, I start a gnome-terminal.  For reference, the hostname is "ubuntu", no biggie I don't really care what it is.  I close the terminal.

I insert my PCMCIA Linksys 802.11b card, go to the Network settings, set up the card as eth1, enter all the settings, and activate the card.  The card hooks up to my access point like a champ.  Then the fun starts.

From this point on, no additional X application will start up.  After rebooting, I'm smart enough to leave up the terminal.  After repeating the Network foo, I attempt to start a random X application via the terminal command line.  I get the following error:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

(gedit:7079): Gtk-WARNING **: cannot open display:

After pulling my hair out and trying a few things, I discover that the hostname gets changed from "ubuntu" to "macaroni" when I activate my wireless card.

The obvious workaround is to enter "sudo hostname ubuntu".  Fortunately the "Run Application..." dialog works even when the hostname changes, so I don't have to remember to bring up a terminal when this happens.  After switching the hostname back to "ubuntu" all X applications work again.

It is 100% reproduce-able and there is a reliable workaround, but it looks to be a serious problem, as I would not expect very many "normal" people to figure this out on their own.  

I am posting this for two reasons:  (1) to help anyone in the same situation, and (2) I am happy to work with someone to help debug this if need be.

Other than this, I just need to figure out how to persist my settings on a USB Key (any helpers out there????) and I'll be very happy with this distro for my Live CD of choice.

Regards,
Greg

---

### Post by ricardo on 2004-10-31
There is a bug report submitted in [https://bugzilla.ubuntu.com/show_bug.cgi?id=2631](https://bugzilla.ubuntu.com/show_bug.cgi?id=2631) about this issue.

I think we have to wait until another version is released.

Regards.

---

### Post by oohlaf on 2004-10-31
[QUOTE=gmilldrum]From this point on, no additional X application will start up.  After rebooting, I'm smart enough to leave up the terminal.  After repeating the Network foo, I attempt to start a random X application via the terminal command line.  I get the following error:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

(gedit:7079): Gtk-WARNING **: cannot open display:

After pulling my hair out and trying a few things, I discover that the hostname gets changed from "ubuntu" to "macaroni" when I activate my wireless card.

The obvious workaround is to enter "sudo hostname ubuntu".  Fortunately the "Run Application..." dialog works even when the hostname changes, so I don't have to remember to bring up a terminal when this happens.  After switching the hostname back to "ubuntu" all X applications work again.
[/QUOTE]

Also see this post [http://www.ubuntuforums.org/showthread.php?t=2232](http://www.ubuntuforums.org/showthread.php?t=2232)

Changing a hostname within a running X server always messes up the X authorization. Kinda stupid the network manager doesn't automatically add the new hostname to the list of magic cookies.

---

