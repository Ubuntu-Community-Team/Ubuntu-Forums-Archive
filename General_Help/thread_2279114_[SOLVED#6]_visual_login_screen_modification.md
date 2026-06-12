---
title: "[SOLVED#6] visual login screen modification"
date: 2015-05-21
forum: General Help
---

### Post by denis40 on 2015-05-21
hi, is there any way to show ip address at the login screen
my ubuntu machine gets ip via dhcp, and i cant make static ip, cause of the configuration of the router (and  yes, i cant influence router settings)
and i want that ip to show up at the login screen

---

### Post by dino99 on 2015-05-21
[http://www.ubuntulinuxguide.com/ubuntu-1204-lts/remote-desktop-12-04-lts/access-ubuntu-remote-desktop/](http://www.ubuntulinuxguide.com/ubuntu-1204-lts/remote-desktop-12-04-lts/access-ubuntu-remote-desktop/)

---

### Post by denis40 on 2015-05-21
thanks for link, but that doesnt help much, it suggests to "Make remote desktop visable to other computers.", but in my Ubuntu 14.04 i dont have "System settings -> Remote Desktop" icon

---

### Post by dino99 on 2015-05-21
login is related to 'user id' not to 'ip' on usual systems; is yours a special one ?

---

### Post by denis40 on 2015-05-21
dino99, i see u didnt get a clue...
imagine a standard login screen, where u supposed to choose login and enter password for it (not console!)
i want to show information about eth0 right at that moment. didnt matter where and how, but exactly before i log in.
and so i was asking is there any way to do this

---

### Post by Holger_Gehrke on 2015-05-21
Take a look at this [page in the wiki]("https://wiki.ubuntu.com/LightDM#Changing_the_Greeter"). You could run a script as greeter-setup-script which generates a wallpaper for the greeter with the IP-address on it (ImageMagick is probably the most versatile tool to do this) then set this file as the wallpaper for the greeter through '/usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override' as described in that page.

---

### Post by denis40 on 2015-05-21
Holger_Gehrke, many thanks
though it's not an easy way, but it'll do what i want ;)
question solved

---

