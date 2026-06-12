---
title: "[SOLVED] Gnome and/or X Malfunctioning"
date: 2008-01-17
forum: General Help
---

### Post by Sidewinder1 on 2008-01-17
Don't know what I did; this happened today and everything was working fine last night. Here are the various symptoms: Upon booting I get an "Nvidia" screen for about 2 seconds prior to login, never seen that before. Once logged in, no matter what window I open it will not drag or resize with cursor. My minimize, maximize, and quit icons are gone from the upper right hand corner of all windows. When I open the terminal I get no prompt or blinking cursor, just a blank screen. I tried rsync from an external hard-drive which I saved about a week ago and no help. This makes me think whatever's wrong may be in grub and not gnome or X desktop. Any assistence would be greately appreciated. Please bear in mind that I'm a total noob to linux; just installed it end of Nov., 2007

---

### Post by jeffus_il on 2008-01-17
> **Sidewinder1 said:**
> Don't know what I did; this happened today and everything was working fine last night. Here are the various symptoms: Upon booting I get an "Nvidia" screen for about 2 seconds prior to login, never seen that before. Once logged in, no matter what window I open it will not drag or resize with cursor. My minimize, maximize, and quit icons are gone from the upper right hand corner of all windows. When I open the terminal I get no prompt or blinking cursor, just a blank screen. I tried rsync from an external hard-drive which I saved about a week ago and no help. This makes me think whatever's wrong may be in grub and not gnome or X desktop. Any assistence would be greately appreciated. Please bear in mind that I'm a total noob to linux; just installed it end of Nov., 2007

You installed the Nvidia restricted driver, You may have had an automatic update running in the background, did you notice a panel icon? You can change the driver in you X configuration by :[LIST]
[*]Opening a terminal window.
[*]Editing  /etc/X11/xorg.conf , changing Device "nvidia" to Device "nv"[/LIST]

---

### Post by Sidewinder1 on 2008-01-17
Thanks for the response. I solved the problem by disabling and then reenabling the nvidia driver from the restricted driver manager menu. Thanks adain. How do I mark this thread as "Solved"?

---

