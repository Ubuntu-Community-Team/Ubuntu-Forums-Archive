---
title: "Please help, major &quot;X server&quot; problems"
date: 2007-10-06
forum: General Help
---

### Post by pvfjr on 2007-10-06
Ok, so I've had this problem before, and didn't really fix it right the first time.  I'm trying to boot up, and I get a blue screen with an error message:  "Failed to start the X server(your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

I think it may have something to do with my video card, but I'm not sure.  I have a Sony Vaio laptop with a ATI Radeon type video card.  Last time this happened I had to reinstall Ubuntu, but couldn't figure out how to do it without wiping the hard drive.  I really don't want to do that this time, as I have a lot of stuff on there I don't want to lose.  I have no idea how to go about fixing this, and am pretty new to the whole linux thing.  Please try to keep it simple for me, I appreciate any help you can give.

---

### Post by pvfjr on 2007-10-06
Ok, nevermind.  I did the "sudo dpkg-reconfigure -phigh xserver-xorg", and it cleared it right up.  I'm still wondering what would be causing this to happen though.  Any insight?

---

### Post by phillips321 on 2007-10-06
usually changes the the xorg.conf file located at /etc/X11 cause the error your describing.

Some applications make changes to that file to adjust resolution, input devices, colour depth etc...

If an app mis configured the file then X11 wont be able to get settings from it correctly.

A good thing to do is once you've got your pc working is:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
then if it even messes up again all you have to do is
```
sudo cp /etc/X11/xorg.cong_backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

any trouble just ask :guitar:

---

