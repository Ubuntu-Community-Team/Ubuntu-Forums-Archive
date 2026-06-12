---
title: "plymouth shutdown flaw"
date: 2016-09-21
forum: General Help
---

### Post by nuggan on 2016-09-21
hi everybody!

os: ubuntugnome 16.04 with gnome 3.18

above all:
i modified the 'ubuntu-gnome-logo.script' file at '/usr/share/plymouth/themes/ubuntu-gnome-logo';
i am aware of that 'update-alternatives --config default.plymouth'- and 'update-initramfs'-stuff;
and it works perfectly well with the daemon tests upon the terminal ('plymouthd; plymouth --show-splash change-mode --boot-up; plymouthd; plymouth --show-splash change-mode --shutdown;')

BUT:
on a real shutdown or restart (haven't tested suspending yet), there firstly appears a static/frozen boot-up screen for a rather long time, then it switches over to the actual scripted shutdown screen for a very short time.

...basically it does everything it is supposed to do - i did'nt even mind if the shutdown screen came late and very short in time. but i can't stand watching the startup-screen telling me 'hi tom' where the shutdown-screen should say 'bye tom' instead.

i was thinking of clearing ram-caches and swap-files but it didnt help.
if there was a mistake within the script the daemon should show - but the daemon shows everything fine.

i suppose there must be some trigger somewhere in the config files that goes wrong or a problem with the graphics architecture or an illness with the x11 engine or a missing .py file or dependency or a tty1 (whatever that means) issue. have found many clues on the forums but none for ubuntu 16.04 (what i have found was stone-old and didnt fit to my os)

any help would be great
cheers
tom

---

### Post by howefield on 2016-09-21
Thread moved to the "*General Help*" forum.

---

