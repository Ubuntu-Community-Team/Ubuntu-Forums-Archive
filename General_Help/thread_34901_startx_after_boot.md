---
title: "startx after boot"
date: 2005-05-16
forum: General Help
---

### Post by joseelsegundo on 2005-05-16
I am trying to get ubuntu to startup in my non-root user's gnome session, without any login.

On gentoo I added a line in local.start:

[FONT=Courier New]su myuser -c 'source /etc/profile;startx'[/FONT]

For ubuntu, I added a script to init.d with that line in it, and installed it using update-rc.d.  No matter where in the boot process I put it, it always failed with
[FONT=Courier New]X: user not authorized to run the X server, aborting.[/FONT]

Is there any equivalent of /etc/conf.d/local.start in Ubuntu?

Thanks -
Rob

---

### Post by dave9191 on 2005-05-16
I dont know about the config files, but Im sure that there is an option on the login manager setup screen in gnome to select a user that gets automattically logged in. I cant provice more accurate info since Im runnign kde.

---

### Post by joseelsegundo on 2005-05-16
Well, not as such, no....  

However, I figured there had to be something like how KDE lets you go straight to a user's session without login, so I poked around some more.  I found what I was looking for in /etc/gdm/gdm.conf:

```
[daemon]
# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=true
AutomaticLogin=myuser
```

rebooted, and voila!

---

### Post by Xian on 2005-05-16
[QUOTE=joseelsegundo]However, I figured there had to be something like how KDE lets you go straight to a user's session without login, so I poked around some more.  I found what I was looking for in /etc/gdm/gdm.conf:[/QUOTE]
For anyone interested, you should be able to make these changes by accessing the gdm setup module, which can be run by following the path listed below from the main panel:

System > Administration >  Login Screen Setup

This is the page you will want to edit. 
Note the 'Automatic Login' section.

[img]http://img.photobucket.com/albums/v469/camplear/forums/gdm.jpg[/img]

---

### Post by Xian on 2005-05-16
[QUOTE=joseelsegundo]However, I figured there had to be something like how KDE lets you go straight to a user's session without login, so I poked around some more.  I found what I was looking for in /etc/gdm/gdm.conf:[/QUOTE]
For anyone interested, you should also be able to make these changes by accessing the gdm setup module, which can be run by following the path listed below from the main panel:

System > Administration >  Login Screen Setup

This is the page you will want to edit. 
Note the 'Automatic Login' section.

[img]http://img.photobucket.com/albums/v469/camplear/forums/gdm.jpg[/img]

---

### Post by dave9191 on 2005-05-17
Thats the setup menu I was talking about :)

---

### Post by joseelsegundo on 2005-05-17
Ah...  I though you meant the login page at boot.  I am so used to text config files, that I didn't think of looking in the System->Administration menu.  :-? 

Thanks for the help

---

### Post by dave9191 on 2005-05-17
Its in the setup files somewhere. If you find it in gconf, then it will be in the dir that gconf stores its settings. But I guess that you arent too bothered about it now :) 

Dave

---

### Post by Xian on 2005-05-17
I use the "Timed Login" option.
I often get busy and forget I booted the puter.

---

