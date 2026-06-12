---
title: "Ubuntu 18.04 fails to load desktop after update"
date: 2019-06-22
forum: General Help
---

### Post by rhauff on 2019-06-22
I ran an update on my old HP/Compaq CQ60 i386 a few months ago, and after reboot it fails to load the graphical desktop.  After the Display Manager starts, I get this screen that seems divided into 6 sections, I cannot switch to a different virtual terminal.  Sometimes Ctrl-Alt-Del will bring a shutdown, but usually I have to hit the power button to escape.
[ATTACH=CONFIG]283468[/ATTACH][ATTACH=CONFIG]283468[/ATTACH]

If i boot to a shell, then run "sudu systemctl start gdm.service", I get a normal desktop.

I am running Nouveau display driver, and have tried disabling Wayland in /etc/gdm3/custom.conf.
I have reinstalled GDM3 and ubuntu-desktop.  I have tried installing LightDM and run "sudo dpkg-reconfigure lightdm" to switch to that instead of gdm3.  None of those helped or changed the problem.

What's the problem??

---

### Post by dino99 on 2019-06-22
What was upgraded ? new kernel, new video codec ?
You might still use the default package (gdm3) and maybe swith to a xorg session. Maybe try a previous kernel, and glance at 'journalctl -b' from a rescue session

---

### Post by rhauff on 2019-06-22
"What was upgraded ? new kernel, new video codec ?"

I don't know what all was upgraded, this laptop is mostly for car work so has all kinds of OBD programs on the windoz partition.  I just let it update last winter, then when boot failed, I just set it aside for a few months.  

"You might still use the default package (gdm3) and maybe swith to a xorg session."

I was under the impression that i was running gdm3 and xorg either way, whether I was booting direct to desktop or booting to shell then  "sudu systemctl start gdm.service".  If I boot to shell then run "sudo gdm3", i get the same locked up screen shown above.

"Maybe try a previous kernel, and glance at 'journalctl -b' from a rescue session"

I'm not sure how to boot a previous kernel or what a rescue session is, I only have 2 boot entries for Ubuntu, default or text mode.  That is a good idea though, I'll expirement with it.  "journalctl -b" might have good info but the problem is when the graphical boot fails and I get the screen shown above, everything is locked up except power button.

---

### Post by rhauff on 2019-06-22
I just tried booting an old kernel, get same wierd locked up screen

---

