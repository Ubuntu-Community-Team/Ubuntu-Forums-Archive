---
title: "Dell Oxtiplex 745 hangs at shutdown and restart"
date: 2008-05-01
forum: General Help
---

### Post by jeremy12 on 2008-05-01
Hi when i was using Ubuntu 7.10 the system worked fine however i did a new fresh install of 8.04 and once it finished installing it hanged indeffinetly at the restart, so i force restarted it HOWEVER it does this when you go to reboot the machine from Ubuntu as well. 

Screen shot of the Shutdown screen:
[IMG]http://i31.tinypic.com/rsvqwy.jpg[/IMG]


Oh:
i did not get this from dell with linux i work for Comcast and we are using ubuntu to do automated backup and restore of 3 partitions that boot into 2000, xp, and vista for customer troubleshooting (so a quad boot system) thats why i posted here and not in the dell area originally

---

### Post by eivindgl on 2008-07-30
Bump, I have the same issue on a series of Optiplex 330 running Gutsy.
Anyone who knows a fix?

---

### Post by jeremy12 on 2008-07-30
Yes there is a a fix for this simply Edit the /boot/grub/menu.lst

look for the OS boot line and add reboot=b to the end of it the line where it says the kernal, UUID, splash, quiet its the longest line

also for refrence 2nd post about this topic
[http://ubuntuforums.org/showthread.php?t=777387](http://ubuntuforums.org/showthread.php?t=777387)

and 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213754)

some people report the reboot=b does not work but it did for me  so its a try, other people have suggested disabling NetworkManager

---

### Post by eivindgl on 2008-07-31
Hi

thanks, it works, what a relief ! :)


[edit] forget the question below;
edit the kopt options in menu.lst and run grub-update
[/edit]
Do you know if this option will get overridden during the next kernel update? if so, is it possible to set this argument as a global default somewhere?

---

### Post by jeremy12 on 2008-07-31
you will get a popup stating you have a modified Grub menu and it will give you the option to keep old or take new, if you take the old then you will not boot using your new kernel so i always just hit use new then go in and modify it

---

