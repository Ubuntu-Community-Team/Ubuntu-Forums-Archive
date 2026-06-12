---
title: "Slow boot: over 4 minutes to get to GDM"
date: 2007-11-24
forum: General Help
---

### Post by alkat on 2007-11-24
Hi.
I've just installed Gutsy on my notebook (nothing special: AMD Athlon XP 1800, RAM 700MB) and I've noticed that it takes forever to load the system. Most other LInux OS I've tried on the same machine takes around two minutes to get to a fully working desktop environment; this Ubuntu installation takes over four minutes just to get to GDM. The weird thing is that during boot the screen stays completely black: no logo and no text is displayed. 

Could anybody give some suggestion on how to fix this problem?

---

### Post by fooman on 2007-11-24
i had similar problem on both of my gateway laptops.  both are amd turions with ati graphics.

on both machines i deleted "quiet" and "splash" from the kernel line in /etc/boot/grub/menu.lst

they boot up quicker then ever now. :)

---

### Post by alkat on 2007-11-24
Thanks,
that worked over here too!

---

### Post by fooman on 2007-11-24
update....i found a better fix!  

first put quiet and splash back into /boot/grub/menu.lst

then check  /etc/usplash.conf and make sure the resolution is set correctly for your screen size.  mine was set @ 1280 x 1024 when my laptop supports 1280 x 800....so i changed the 1024 to 800.   

change it to what your screen supports and save the change.

after you change the resolution to the correct size,  run this command: 

```
sudo update-usplash-theme usplash-theme-ubuntu
```

reboot and you should have the splash screen back with a much faster boot time.  :)

i found this fix here (so a thank you to the original poster :)):  [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

