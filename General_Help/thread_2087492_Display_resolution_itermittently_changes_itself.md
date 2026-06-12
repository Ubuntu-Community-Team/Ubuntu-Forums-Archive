---
title: "Display resolution itermittently changes itself"
date: 2012-11-23
forum: General Help
---

### Post by mb_webguy on 2012-11-23
Relevant info:
Ubuntu 12.04 x64
ATI Radeon HD 4290 video card using the proprietary FLGRX driver

Problem:
I have a computer I'm using as a media and web server.  It's connected to my tv using HDMI, but I primarily access using VNC over ssh.  For better readability both over VNC and when using the tv as a monitor, I set the display resolution to 720p instead of the tv's preferred max of 1080p.  After some recent updates, the display resolution automatically changed to 1080p while I was connected using VNC.  I used Catalyst Control Center (using gksudo) to change the resolution back to 720p, but after a while it changed itself back to 1080p again.

I considered that it might be a VNC issue, but it happens while using the tv as a monitor as well.  There are quite a few posts in the forums where people have reported similar problems, but all of those seem to involve the resolution resetting after a reboot or when waking from suspend, while mine changes *while I'm using the computer*.  I haven't noticed any pattern to when the resolution resets itself; it might reset itself after five minutes or five hours, and it doesn't seem to be caused by anything I'm doing with the television.  

Even if this is the same problem as in the similar posts, none of the posts I found offered a solution.  And I have no idea if the problem is hardware- or software-based.  All I know is that it's really annoying, and it only started happening about a week ago, and all that I did to the computer in that time was install some updates.

I've made an alias for "sudo xrandr -s 1280x720" so I can quickly fix the resolution back when it changes itself, but this isn't really a solution.  Any ideas?

---

