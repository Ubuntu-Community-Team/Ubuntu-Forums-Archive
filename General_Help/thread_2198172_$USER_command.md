---
title: "$USER command"
date: 2014-01-07
forum: General Help
---

### Post by cmcanulty on 2014-01-07
I finally fixed my system with the following commands I got off a link. I couldn't login to anything except xbmc as I had autologin on and xbmc took up the whole screen and wouldn't let me get to a terminal by keyboard shortcut or get anywhere by esc or rt click so I needed to disable autologin and then get to ubuntu and remove xbmc. It worked but took all morning.I booted to a live USB and then used the below commands and then changed a config file on my installed /partition to stop autologin. What I want to know is how to understand how the commands let me mount and edit my / when I couldn't do it before the commands in a live boot. I hope that's not too confusing. Thanks
```
sudo mkdir /media/$USER
sudo chown $USER.$USER /media/$USER
```

---

### Post by tfrue on 2014-01-07
If you did this during a live boot you should've been able to mount and edit the / partition without those commands as it takes root permissions to mount anyway. But what you did was create a directory named after the variable $USER, as defined with the command ```
printenv | grep USER
```

You then changed the owner and group of the directory you just created to the USER variable, but what I'm saying is when you mount the / partition, you would have to use sudo which would give root permissions to that entire directory.

I don't understand what you did after the commands that made you able to edit your system? Did you mount your HDD from a live boot then edit the files? Or did you do those commands then mount your HDD under the /media/$USER directory. Can you now boot into your system and access a terminal without live booting?

---

### Post by cmcanulty on 2014-01-08
The reason I didn't understand is when I did mount it as you said I didn't have permissions to alter it, after the commands it mounted  I did have read write access. I needed to disable autologin as it had me stuck in xbmc a media player and no way to get out of it so I edited the login file and then logged in and deleted xbmc which is big trouble. No way to esc, get terminal by ctl+alt+t  and no way to exit full screen so computer was unusable, thanks

---

