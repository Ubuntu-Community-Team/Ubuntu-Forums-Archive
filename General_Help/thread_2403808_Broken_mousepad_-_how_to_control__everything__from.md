---
title: "Broken mousepad - how to control _everything_ from keyboard"
date: 2018-10-16
forum: General Help
---

### Post by drglas2 on 2018-10-16
Hi,

I have an old Lenovo x240 that I spilled coffee all over a few years back. This caused the mousepad to stop working. (What's funny is that even an external mouse does not work :() My plan now is to do a clean Ubuntu install on this machine and utilize it as a plex media server since the laptop is quiet and powerful enough for realtime transcoding. However...I have no way of controlling the computer with internal nor external mousepad/mouse. 

I've been running Raspbian on my RasberryPi and *that *system I managed to configure so that I could use the keyboard for moving the mouse cursor. Not numpad, but keys I configured myself...my Lenovo laptop does **not **have a numpad.

My question is if it is possible to setup Ubuntu in a similar way. Note however, that I have no mouse _ever_. So everything from initial Ubuntu installation to Plex media server setup must be controlled only from keyboard. Would this even be possible?

I have managed to install Ubuntu 18.04 on the Lenovo by only using keyboard. But then I'm stuck since (I think) Ubuntu is not made for no-mouse operation.

Any suggestions?

N

---

### Post by TheFu on 2018-10-16
A few ideas. You've probably considered these already.

Have you tried using a different USB port, perhaps on the other side of the laptop?  It could simply be that the USB controller is fried, so using the other one might solve it?

Plex media server is a server. No GUI needed.  You can manage it through the web interface on port [http://ip:32400/web](http://ip:32400/web)  Do the install and setup an ssh server, then just ssh into the laptop and configure stuff like a normal Linux server. No GUI.  If that is beyond your current skill, install x2go-server on it and use an x2go-client from any other desktop/laptop to manage it.  No video will work well, but that isn't the point.  Use the x2go PPA and follow those installation instructions.  Get ssh working first.  x2go works like every other NX protocol and requires ssh.

Plex has a client, which works with a 10 ft interface.  I've never used a mouse with it, but I do have an RC-6 media remote.
I'm not a fan of any Plex clients for a number of reasons, but the main reason for me was that I watch many foreign films with subtitles. Whenever pausing playback under plex, their on-screen info pops up over all the subtitles which prevents reading them.
Instead, I use Kodi as a Plex client using the PlexBMC addon.  Kodi works with the remote from a 10ft interface too.  My kodi machines don't have keyboards or mice connected, just a USB remote control, though I suppose a Bluetooth media-remote keyboard+touchpad would work, perhaps.  I've never used one myself.  For remote control I just use the RC-6 device, but I've played with the Kodi web interface, Plex web interface and Kodi apps.  In the end, ssh into the kodi & plex machines are how I patch and configure everything and the RC-6 remote is how playback is handled.

Just some options for your consideration.

---

### Post by drglas2 on 2018-10-17
Hi TheFu, and thanks for input. I doubt it is only the USB controller but I'll check!

I'm relatively skilled in Linux, so setting everything up via ssh shouldn't be a problem. I started trying to get a vnc server up and running but ssh makes more sense of course. Thanks.

On the topic of Plex...Interesting input! I use plex when I want to stream to one of my devices while I'm not at home, and then I use Kodi for watching movies at home. Was not aware about the PlexBMC addon but I'll investigate it. 

N

---

### Post by HermanAB on 2018-10-17
Well, if you install a server version of Ubuntu, then you have no GUI and don't need a mouse.

---

### Post by TheFu on 2018-10-17
> **drglas2 said:**
> Hi TheFu, and thanks for input. I doubt it is only the USB controller but I'll check!

I'm relatively skilled in Linux, so setting everything up via ssh shouldn't be a problem. I started trying to get a vnc server up and running but ssh makes more sense of course. Thanks.

On the topic of Plex...Interesting input! I use plex when I want to stream to one of my devices while I'm not at home, and then I use Kodi for watching movies at home. Was not aware about the PlexBMC addon but I'll investigate it. 

N

Well, if an external USB keyboard and/or external USB mice don't work, what else could it be if the computer actually still works?  That was my thought process there.

I never use VNC without either an ssh-tunnel or full VPN.  vnc-server has a --localhost option to force the remote user to gain local access before allowing insecure remote VNC connections.  Use it, know it, love it.  VNC isn't secure any other way.   Or just use x2go.

It is easy to stream from Plex when not at home without having a plex account or plex userid or plex client.  Either use an ssh tunnel and the web interface or use a full VPN.  I've posted my ssh-tunnel script which works as a SOCKS proxy here a few times already. Searching these forums for "**export http_proxy="socks5://localhost:64000";**" should find it, I'm guessing.

---

### Post by drglas2 on 2018-10-21
Got everything up and running. Thanks for input!

---

