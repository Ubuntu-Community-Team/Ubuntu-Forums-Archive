---
title: "login screen has huge fonts"
date: 2008-05-19
forum: General Help
---

### Post by cnstarz on 2008-05-19
Does anyone know how to fix this?  After I login, the screen res/font dpi is fine.  Its just the login screen that experiences this problem.

[IMG]http://cool.lololcats.com/random_images/login.jpg[/IMG]

---

### Post by cnstarz on 2008-05-19
bump from page 12

---

### Post by nick_h on 2008-05-20
In gnome, you can add a -dpi option to the X server command in the gdm.conf file.

I think you can do the same with kde in your kdmrc file.

---

### Post by Zorael on 2008-05-24
Yes. Open up [FONT="Courier New"]/etc/kde3/kdm/kdmrc[/FONT], find the line **ServerArgsLocal** and append **-dpi 96** to it.
```
ServerArgsLocal=-nolisten tcp -dpi 96
```

---

### Post by jimbob on 2008-05-24
This fixed it for me:

Another solution might be to add the line
Code:

	
Option  "DDC" "No"

in Section "Device" in the file /etc/X11/xorg.conf. This works at least for me with the open source radeon driver.

You can edit the file from the terminal with nano,
Code:

sudo nano -B /etc/X11/xorg.conf

Since it is made in xorg, it ought to work for Kubuntu also.

---

### Post by rpwdh on 2008-06-22
> **jimbob said:**
> This fixed it for me:

Another solution might be to add the line
Code:

	
Option  "DDC" "No"

in Section "Device" in the file /etc/X11/xorg.conf. This works at least for me with the open source radeon driver.

You can edit the file from the terminal with nano,
Code:

sudo nano -B /etc/X11/xorg.conf

Since it is made in xorg, it ought to work for Kubuntu also.

jimbob,

YOU ROCK!! :guitar:

This has been driving me nuts for weeks!! ](*,)

---

