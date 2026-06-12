---
title: "fstab mounted shares on all desktops"
date: 2007-08-20
forum: General Help
---

### Post by reckless2k2 on 2007-08-20
i have a kubuntu system with 5 users that log in locally or remotely run X over ssh. i mounted a remote share for 2 users to access. the share is only viewable by these users but the mounted share shows up on every desktop. the other 3 users get a permission error if they try to access the icon that appears on their desktop. i want it so the share only shows on the desktops that have permissions to access. is this possible? to me it's a security issue because they can see the share information (route, IP, etc.). 

thanks.

---

### Post by reckless2k2 on 2007-08-21
for anyone that might care how i resolved this...i fired up kcontrol with sudo privledges and killed showing samba mounted shares from showing on the desktop. then on the users with access, i just created icons to the location. it was a little easier than i thought after i thought about it. i guess it was kind of a silly question and that's why no one answered it.

---

