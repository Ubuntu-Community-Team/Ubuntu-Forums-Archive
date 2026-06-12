---
title: "Lubuntu 12.10 default autostart programs"
date: 2013-03-13
forum: General Help
---

### Post by sarar on 2013-03-13
Can anyone tell me the default autostart programs in Lubuntu 12.10? When I tried to add a program to /etc/xdg/lxsession/Lubuntu/autostart and then rebooted, everything had mysteriously disappeared from the file and I'd like to put it all back.

---

### Post by Rex Bouwense on 2013-03-13
I think you may find what you want here;
[http://ubuntuforums.org/showthread.php?t=1984904](http://ubuntuforums.org/showthread.php?t=1984904)

---

### Post by sarar on 2013-03-13
Nope, I just need someone with Lubuntu 12.10 to look at their /etc/xdg/lxsession/Lubuntu/autostart file and tell me exactly what's in it (minus anything they've added).

---

### Post by Bashing-om on 2013-03-14
sarar; Hi !
May not help .....but Here is mine from 12.04 ....maybe sane same ...
```
sysop1@1204-a:~$ cat /mnt/backup/buntu-autostart
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
sysop1@1204-a:~$ 
```[INDENT=2]
Just hope it helps

[/INDENT]

---

### Post by sarar on 2013-03-14
Thank you so much, that seemed to do it!

---

### Post by sarar on 2013-03-14
Although if anyone out there has 12.10 and could verify that this is correct, I would appreciate it.

---

### Post by Rex Bouwense on 2013-03-14
This is from Lubuntu 12.10.
> 
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

Hope that is what you want.

---

### Post by sarar on 2013-03-14
Yep, that's it. Thank you.

---

### Post by Bashing-om on 2013-03-14
sarar; Good to Go ?
Yepper ! ...please mark this thread as solved, aids others seeking info and the helpers here time in not looking at a solved situation.
[INDENT=3]
just try'n to help

[/INDENT]

---

