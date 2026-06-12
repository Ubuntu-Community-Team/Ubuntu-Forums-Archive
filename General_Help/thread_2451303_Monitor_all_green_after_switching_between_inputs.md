---
title: "Monitor all green after switching between inputs"
date: 2020-10-01
forum: General Help
---

### Post by jdderby2 on 2020-10-01
I have 2 dual port monitors, one port on each monitor is connected  to a work PC, and one port on each monitor is connect to my Ubuntu 20.04  machine.  Occasionally the when I try to switch back to the Ubuntu side  the monitors are all green.  I can't get to a login screen or anything  and ultimately have to force a reboot.  I am looking for some  suggestions on where to start troubleshooting. 				

I found think in the logs:


Sep 28 16:00:06 tux kernel: snd_hda_intel 0000:0a:00.1: Refused to change power state, currently in D0
Sep 28 16:00:09 tux kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR*  ring gfx_0.0.0 timeout, signaled seq=7506282, emitted seq=7506284
Sep 28 16:00:09 tux kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR*  Process information: process Xorg pid 1755 thread Xorg:cs0 pid 1757
Sep 28 16:00:09 tux kernel: [drm] GPU recovery disabled.
Sep 28 16:00:24 tux gsd-xsettings[2136]: Failed to get current display configuration state: Timeout was reached

---

### Post by HermanAB on 2020-10-02
Check the cables.  The computer talks to the screen over a serial port to get the screen capabilities.

---

### Post by jdderby2 on 2020-10-12
The cables are fine, if I switch to the other input all is good, can see video on windows machines.  I have tried swapping the cables between windows/Ubuntu machine still same result.  Also I have noticed the Ubuntu session is still live except the video, I can still hear audio.  Any other ideas to help troubleshoot this issue?  Both connections are over HDMI one of which is also through a display port, other is HDMI direct to video card.  Is there a service I could try to restart via ssh from another device?

---

### Post by BFG on 2020-10-13
> **jdderby2 said:**
> I have 2 dual port monitors

Generally monitors are not dual port. They have alternative ports to satisfy different connectivity standards. I.e. they are designed to only use one at a time.   

When you have green screen, disconnect and reconnect the ubuntu cable. If no change. Disconnect the windows cable and leave it disconnected. Then repeat - disconnect and reconnect the ubuntu cable.
If the problem persists, ubuntu setup is the right place to look. If the video restores, most likely you're hitting a hardware limitation with the monitor.

---

