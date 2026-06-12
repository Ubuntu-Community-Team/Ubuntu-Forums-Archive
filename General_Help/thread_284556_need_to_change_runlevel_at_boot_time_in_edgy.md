---
title: "need to change runlevel at boot time in edgy"
date: 2006-10-25
forum: General Help
---

### Post by Deus42 on 2006-10-25
I have been stumped by this for a couple days now:

I need to be able to change the runlevel of edgy at boot to accommodate different xorg.conf files for my laptop.

In dapper, I could simply append the runlevel number to the end of the kernel line in grub and it would boot. In edgy however, it always boots to runlevel 2.

Does anyone have any ideas?

- Chris

---

### Post by Deus42 on 2006-10-26
Well the reason I was doing this was so that when my computer was running in a docking station, I could have a different xorg.conf file. I ended up working around the problem by writing a startup script to detect if a particular piece of hardware was plugged in, and if so, reconfigure X.

Does anyone know if there is a better way to do this?

---

### Post by tuxcantfly on 2006-10-26
how about you control-alt-F1 after you boot, edit your /etc/X11/xorg.conf, and restart?

---

### Post by fangorious on 2006-12-12
if your X config is busted to the point of not being able to do anything but reboot, and you want a full networked/multi-user command-line login to fix it.

---

### Post by Deus42 on 2006-12-12
The idea is I want to reconfigure xorg.conf AT BOOT, it wouldn't be practical for me to boot up, reconfigure X by hand, and then reboot every time I put my laptop in the docking station.

So far though, my script to reconfigure X using with a startup script that detects the docking station's hardware is working great.

Thanks,

Chris

---

