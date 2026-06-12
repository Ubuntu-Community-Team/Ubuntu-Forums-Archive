---
title: "&quot;Could not start X server...&quot;"
date: 2007-01-10
forum: General Help
---

### Post by nevin on 2007-01-10
yesterday, my linux crashed... it gave me a plain black screen out of no where... I didn't even do anything to cause it.  So, i turned my computer off and turned it back on, and when it loaded, i got this blue screen that said:

[INDENT]```
Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled.  Please restart GDM when
the problem is corrected.
```[/INDENT]

now i could understand getting this message if i had messed with the xorg.conf file or something, but the only thing i can think of, i installed lame with apt-get.  that's it.

i have (had) beryl with an ati card, and everything was working fine... for a couple of months now.

i really have no clue how this happened, and i was wondering what to do.

do i need to fix my xorg.conf file?  if i do, will it mess up my beryl/monitor resolution?  or is it something else?

any help would be greatly appreciated!

---

### Post by riven0 on 2007-01-10
You didn't say whether you already did **sudo dpkg-reconfigure xserver-xorg** yet. That'll be the first step to take.

---

### Post by nevin on 2007-01-10
is that going to mess up my beryl set up?

---

### Post by nevin on 2007-01-10
i did

[INDENT]```
sudo dpkg-reconfigure xserver-xorg
```[/INDENT]

and i got all the way through it and then it says it cant write the xorg.conf file because the disk is read-only.

what am i supposed to do with that?

---

### Post by cmost on 2007-01-10
I think you might have installed the xorg update that requires you to reinstall your graphics driver.  Others have been complaining about this throughout the forum today.  Things rarely just "crash out of nowhere."  Hope this helps!

---

### Post by nevin on 2007-01-10
i tried copying the xorg.conf file from the live disc over to my system, but it didn't work... i reallly have no idea of where to go from here.  outside of reinstalling, but that's not something i really want to have to do.

should i try copying the gdm.conf file as well?

---

### Post by Beernut on 2007-01-10
Seems yesterdays updates killed a lot of systems.  Check out this thread [http://www.ubuntuforums.org/showthread.php?t=334839&highlight=update](http://www.ubuntuforums.org/showthread.php?t=334839&highlight=update)

---

