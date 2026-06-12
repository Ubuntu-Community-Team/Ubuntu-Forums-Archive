---
title: "tutorial request"
date: 2007-03-30
forum: General Help
---

### Post by Coinz on 2007-03-30
Hi, i cant find a newbie frienly tutorial on how to change mouse polling rate and resolution on boot for ubuntu ( gento for exemple has one [http://gentoo-wiki.com/HOWTO_Customize_Mouse_Polling_Rate](http://gentoo-wiki.com/HOWTO_Customize_Mouse_Polling_Rate) )

this is very usefull for gamers that are migrating from windows to linux like me. So here is the request. Hope someone do it :)

ps: my mouse is a logitech mx518

---

### Post by dbbolton on 2007-03-30
did you check the tutorial/howto section of the forum ?

---

### Post by Nikron on 2007-03-31
> **Coinz said:**
> Hi, i cant find a newbie frienly tutorial on how to change mouse polling rate and resolution on boot for ubuntu ( gento for exemple has one [http://gentoo-wiki.com/HOWTO_Customize_Mouse_Polling_Rate](http://gentoo-wiki.com/HOWTO_Customize_Mouse_Polling_Rate) )

this is very usefull for gamers that are migrating from windows to linux like me. So here is the request. Hope someone do it :)

ps: my mouse is a logitech mx518

try lomoco

---

### Post by Coinz on 2007-03-31
thanks, lomoco does the job for the resolution issue now i have to figure out how to change mouse polling rate,

btw in the gentoo toturial they say: 

Grub

    You need to append "usbhid.mousepoll=2" to the kernel section of your kernel in your /boot/grub/grub.conf file.

but i cant find grub.conf

```
coinz@coinz-desktop:~$ locate grub.conf
/usr/src/linux-headers-2.6.17-10/debian/examples/kpkg_grub.conf
/usr/src/linux-headers-2.6.17-11/debian/examples/kpkg_grub.conf
coinz@coinz-desktop:~$ 

```

---

### Post by Coinz on 2007-04-01
i found a way to change mouse polling rate here [http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)

thanks for the support

---

