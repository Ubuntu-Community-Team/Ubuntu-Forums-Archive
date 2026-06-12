---
title: "Ubuntu 22.10 - Night Light Not working"
date: 2022-11-23
forum: General Help
---

### Post by maglin2 on 2022-11-23
Intel® Core™ i3-10100 CPU
Intel CometLake-S GT2 [UHD Graphics 630] Display, i915 Driver

Turning Night Light on/off has no effect. Neither does adjusting display temperature.

Location is turned on.
Using wayland, but I've tried Xorg but it still doesn't work.
I tried changing display temperature in dconf-editor, but that didn't have any effect either.

Any ideas on what else I might try to get it working (or at least find out why it isn't working) appreciated.

---

### Post by Dennis N on 2022-11-23
It won't turn on (manually or automatically) unless the current time is between the ON and OFF times shown in Settings > Display > Night Light.

---

### Post by maglin2 on 2022-11-23
That is currently the case. 
It's 18.50 here.  
It should have turned on at 15.54, but it's not working (despite showing as on - it does nothing to alter display).
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291291&stc=1[/IMG]

---

### Post by Dennis N on 2022-11-23
I checked using the manual option on 22.10, and can confirm it's not working. I will have to wait and see on the "sunrise to sunset" option.

**Update:** I checked Manjaro Linux and the night light works there with the manual setting (the only one I could test). It could be a bug in the version of gnome-shell (43.0), or Ubuntu's implementation. Manjaro has gnome-shell 43.1, while Ubuntu 22.10 has 43.0.

**Update 2**: See post #6

---

### Post by maglin2 on 2022-11-23
Thanks for checking it.

---

### Post by Dennis N on 2022-11-23
_Update to remarks in post #4_:

The reason my night light test failed in post #4 was because the Ubuntu 22.10 I used was in a virtual machine. I think the guest is unable control the screen brightness or color temperature; only the host can do that.

I have another Ubuntu 22.10 installed on another computer which is a regular install. Using this, I found that the night light does work correctly!

So, is your Ubuntu installed in a virtual machine? That would explain the night light failure. If not, the cause is yet to be found. At this time, I have not thought of a possible cause.

---

### Post by maglin2 on 2022-11-24
This is a bare metal install, full disc encryption.

Bit of background. I normally stick to LTS releases, but I was forced to 22.10 on this machine because the graphics driver module wouldn't load without kernel 5.18 and above. Slightly confused discussion here (look toward the end)
[https://ubuntuforums.org/showthread.php?t=2479806&page=2](https://ubuntuforums.org/showthread.php?t=2479806&page=2)

---

### Post by maglin2 on 2022-11-24
I just tried a Kubuntu 22.10 live USB in the machine and Night Colour (as it's called in Plasma) works correctly.
So this is something to do with gnome.
If the machine you tested with was also gnome, then it's specific to gnome on this machine and machines sharing the relevant characteristic (whatever that is).

---

### Post by maglin2 on 2022-11-26
I've got a crude workaround using sct with day and night temperature keyboard shortcuts, but any pointers on how to investigate why the system isn't working as designed appreciated.

---

### Post by maglin2 on 2022-12-09
I 'solved' this by switching from gnome to plasma desktop, in which night light works (including with wayland).
This isn't a really a solution, but it does suggest (to me at least) that it isn't (entirely) a hardware compatibility issue.
It doesn't seem to be a misconfiguration issue, since it arises with the live USB and with a fresh install.
It isn't exactly the same issue as any current bug I could find.
I have therefore raised a bug. [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1998344](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1998344) 
In the event anyone else finds it applies please add your name.

I have no real expectation that the bug will be fixed if it affects very few users, but I am currently marooned on 22.10 with this machine (since graphics driver module won't load with 22.04 or 20.04).
I thought I'd better get some practice in raising bugs, and keep a close eye on the testing of 23.04 etc, in case there is a regression to the graphics driver module not loading again!
I'll also keep an eye on 22.04.2 development and hope for a pleasant HWE stack surprise.

---

### Post by maglin2 on 2023-02-16
Switched to Ubuntu 22.04 following its recent update to kernel 5.19 (same as 22.10) and the night light now works!
(It never did work with 22.10)

---

