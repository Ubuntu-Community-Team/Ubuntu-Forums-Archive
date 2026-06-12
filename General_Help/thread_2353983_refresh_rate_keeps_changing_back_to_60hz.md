---
title: "refresh rate keeps changing back to 60hz"
date: 2017-02-27
forum: General Help
---

### Post by vindiesel756 on 2017-02-27
Hello,
i have Ubuntu 16.10, Using NVIDIA binary driver - version 367.57 from nvidia-367 (proprietary,tested).
I tried change it with xrandr and in nvidia x server settings to 144hz and save it to xconf file as superuser, but it keeps reverting back to 60hz after restart.
Any ideas thanks.

---

### Post by vindiesel756 on 2017-02-28
I found possible solution: [http://askubuntu.com/questions/126928/system-reverts-to-87hz-refresh-rate-at-every-startup-after-i-have-installed-nvid](http://askubuntu.com/questions/126928/system-reverts-to-87hz-refresh-rate-at-every-startup-after-i-have-installed-nvid)
But if i open lightdm.conf with sudo i see blank file and i need paste this command to last line, i tried just paste it and save it and than i couldn't boot with gui.
I have no idea why i can't see anything in this file, because i used sudo...

---

### Post by howefield on 2017-02-28
You have to be careful when using such a recent release but following such an old tutorial.

Generally when you get an unexpectedly blank file for editing it means that the file doesn't exist, or of course is indeed blank :)

Please post the terminal input/output of what you are trying to do.

---

