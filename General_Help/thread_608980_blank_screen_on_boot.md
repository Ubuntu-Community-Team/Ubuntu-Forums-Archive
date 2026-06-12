---
title: "blank screen on boot"
date: 2007-11-10
forum: General Help
---

### Post by Rock on 2007-11-10
i am running kubuntu 7.10 and i just restarted my computer and i just get a black screen. before, i restarted everything was fine. btw, i have tried restarting it lots of times. so what could the problem be and how do i fix it without reformatting?

---

### Post by dboot on 2007-11-10
Any change in your graphics card drivers? If mine isn't set up correctly, I'll get a blank screen (which means gdm didn't start properly). Since I have an nvidia graphics card, a quick fix is to edit my /etx/X11/xorg.conf file and change the driver from "nvidia" to "nv". 

After turning on your computer, try pressing CTR+ALT+F1 or F2. If you get the CLI (command line) then most likely gdm isn't starting because of your xorg. conf file. Before you change anything in the file, be sure to back it up. If you don't get the CLI, keep asking around.

---

### Post by misfitpierce on 2007-11-10
This seems to be pretty common problem with Gutsy... Boot up and at grub screen hit esc to get to grub screen. Hit e on main boot partition, hit e on 2nd one down again should be longest command one,... Change splash at end to nosplash and boot up. Then when inside Ubuntu try this in terminal....

sudo gedit /etc/usplash.conf
Change the res to your reso.
save and close
sudo update-initramfs -u

---

### Post by tom957 on 2007-11-10
misfitpierce, thanks!

---

