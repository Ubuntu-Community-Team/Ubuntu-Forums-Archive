---
title: "How do I have the system create a link on inserting a device?"
date: 2007-01-19
forum: General Help
---

### Post by donkyhotay on 2007-01-19
When I plugin my gamepad ubuntu assigns it to /dev/input/js0 which is fine for most things however one of my programs searches for gamepads at /dev/js0 and doesn't find it at /dev/input/js0. To work around this after plugging in my gamepad I simply create a link where my game searches for the gamepad however whenever I reboot my system or unplug my gamepad the link vanishes (this happens even when I use a soft link and by my understanding of soft links they should remain even when the original "file" is removed). What I want to know is how do I either create a permanent link that will remain even after removing my gamepad or have a small script run when I plugin my gamepad so it automatically creates the link for me without me having to run my script manually all the time.

---

### Post by mssever on 2007-01-19
Soft links don't work because in the 2.6 kernel, /dev isn't a real filesystem. It's more like /proc (ie, created on the fly). There is a way to script that, though...I don't remember it at the moment, but I'll post back when I do.

---

### Post by mssever on 2007-01-19
OK... Configuring udev is what you're after. See this post: [http://ubuntuforums.org/showpost.php?p=1537617&postcount=6](http://ubuntuforums.org/showpost.php?p=1537617&postcount=6). Also, read the udev man page. You should be able to figure it out from there.

---

### Post by donkyhotay on 2007-01-19
Thanks, I'm not familiar with udev configuration but I found on another thread that adding 

# Create Joystick /dev/js0, /dev/js1, etc using symlink 
#(links /dev/input/jsX to /dev/jsX)
KERNEL=="js[0-9]*", SYMLINK+="%k"

to /etc/udev/rules.d/60-symlinks.rules works.

---

