---
title: "Firefox having issues when resuming from suspend."
date: 2017-05-10
forum: General Help
---

### Post by Roasted on 2017-05-10
Hi friends. I'm having an issue in Firefox, and have been experiencing this issue, for quite some time. I'm curious if anybody else has experienced it and whether they know of a workaround besides switching to Chrome (which is tempting at the moment).

The issue is this. Using a laptop with Firefox running, I often suspend the laptop, move to another location, plug in a 2nd display, and resume the laptop. Upon resuming, Firefox will not redraw the browser window. As I click on other tabs, the title bar changes, suggesting Firefox acknowledges this action, but it doesn't draw the window to show me that tab. If I click on another application to redirect focus, suddenly Firefox redraws the window. This happens when I connect a 2nd display while suspended and then resume, as well as resuming my laptop, touching/clicking nothing, and then plugging in a 2nd monitor.

I've duplicated this on Ubuntu 16.04, Ubuntu Gnome 17.04, and two different laptops (Dell Latitude, Lenovo T470). 

I find it difficult to verbalize exactly what I'm experiencing, and likewise I've found it difficult to dig up bug reports relating to this. I did find a past Firefox bug who's title sounded relevant, but that bug report 404'd me. I took a screencast to really capture what's happening.

In the case of this video, I had Firefox + 4 tabs running. I then suspended the laptop. Afterwards, I connected a 2nd display and resumed (again, this often happens if I resume and connect a 2nd display after). Then I fired up Kazam and began recording what was happening.

It's also worth noting that when this happens, I cannot recover Firefox at all, or even launch it as normal. I must kill the Firefox process (even though Firefox is visibly closed), and then relaunch it to operate normally again.

[Video here.]("https://drive.google.com/open?id=0B96Ld5Ukgbx8UVRaV1liWjFBeFU")

Any ideas?

---

### Post by howefield on 2017-05-10
I see something similar with Firefox resuming from suspend.

Generally a click on the launcher icon to minimise and another click to restore the window does the trick.  Haven't been too bothered by it to seek a fix tbh so not sure if it is the open source video driver, firefox or something else altogether.

---

### Post by Roasted on 2017-05-10
I just tried that, but it didn't make a difference on my end. :( No matter what tricks I try or what I click on, I can't get Firefox to begin to act normal unless I kill it entirely and bring it back. I just tested the same scenario but with Chrome running with multiple tabs, and I resume just fine and pick up where I left off. I'm trying to resist switching, but this isn't easy. :(

---

### Post by Skerit on 2017-06-28
I have the same issue, in Ubuntu 17.04 using Unity and in Ubuntu Gnome 17.04 using Gnome-shell.

I am using the open-source AMDGPU drivers.

---

