---
title: "network packets blocked"
date: 2007-10-11
forum: General Help
---

### Post by infurno on 2007-10-11
Hello, im having some network trouble... Im not sure if anyone here can help but i have been working on this for hours...

Im trying to use an Elphel 333 ethernet camera to aquire video. Im able to connect to the cameras web based interface to set settings and get preview images of what the camera sees. There I start the RTSP streamer.

mplayer and mencoder are both able to connect to the camera but will not show any video. VNC will also connect but not show video. The stream is there for sure, and a lot of data is getting sent 2000x800 pixels at 24 fps but the network history under the system monitor is blank.

The netwok activity light is flashing on the camera, and its also flashing on the NIC but ubuntu must be ignoring or blocking the packets getting broadcasted.

Last time this happened was on Windows and i had forgot to disable a firewall. Once the firewall was disabled, everything worked.

How do you set ubuntu not block/ignore the packets?

Any advice would be appreciated.

---

### Post by dcstar on 2007-10-11
> **infurno said:**
> Hello, im having some network trouble... Im not sure if anyone here can help but i have been working on this for hours...

Im trying to use an Elphel 333 ethernet camera to aquire video. Im able to connect to the cameras web based interface to set settings and get preview images of what the camera sees. There I start the RTSP streamer.

mplayer and mencoder are both able to connect to the camera but will not show any video. VNC will also connect but not show video. The stream is there for sure, and a lot of data is getting sent 2000x800 pixels at 24 fps but the network history under the system monitor is blank.

The netwok activity light is flashing on the camera, and its also flashing on the NIC but ubuntu must be ignoring or blocking the packets getting broadcasted.

Last time this happened was on Windows and i had forgot to disable a firewall. Once the firewall was disabled, everything worked.

How do you set ubuntu not block/ignore the packets?

Any advice would be appreciated.

AFAIK there is no default firewall installed in Ubuntu, your problem is probably a missing codec for the type of video you are trying to use.

---

### Post by infurno on 2007-10-11
I can play videos recorded with this camera when booting from the livecd. Its just OGG. Im also using software that is provided by the camera manufacturer.

I can use wireshark and view all the packets coming from the camera but none of the software will pick it up. very strange.

---

