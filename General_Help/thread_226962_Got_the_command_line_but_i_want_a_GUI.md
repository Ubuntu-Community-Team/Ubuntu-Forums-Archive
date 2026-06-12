---
title: "Got the command line but i want a GUI"
date: 2006-08-01
forum: General Help
---

### Post by smee56 on 2006-08-01
Help im only new at ubuntu but i need to find out how to get the Gui from the command line 
If any one could help it would be much appreciatted

Smee56=;

---

### Post by sethmahoney on 2006-08-01
Did you install the server edition or the desktop version?

---

### Post by catlett on 2006-08-01
If you installed the desktop cd but for some reason you are at a text based login, login with your user name and password. Then enter this command to start the x window system ```
startx
```If that returns an error, then you have a server install and you need to insatll the desktop. This is easy as long as you have an internet connection. Log in and enter this ```
sudo aptitude install ubuntu-desktop
```That will install everythiung ytou need to have a gui environment. You mau have toi reboot, I don't remeber.

---

### Post by sethmahoney on 2006-08-01
Well, there are other reasons it might return an error - if you do get an error when you type startx, copy it down and post it to this thread.

Also, if you're dual-booting and getting annoyed resetting your computer every time you want to post to this thread, after you log in type

sudo apt-get install lynx

and then, once that's done, type

lynx

and that will give you a text-based web browser that you can use to scan the forums for help.  Its a pain in the ***, but sometimes less so than rebooting every five minutes.

---

### Post by smee56 on 2006-08-01
thanks all 

Smee56

---

### Post by smee56 on 2006-08-02
hey it didnt work but heress what happened 

daniel@ubuntu ~$startx
xauth: creating new authority file /home/daniel/severauth.8575

fatal sever error:
server is allready active for display 0
if this server is still running, remove /tmp/.X0-lock
and start again.

please consult........so on so on...

xlib: connection to ":0.0" refused from server

xlib: invalid MTI-MAJIC-COOKIE-1 giving up
xlib: unable to connect to xserver

no such process (errno 3):server error](*,)

---

### Post by catlett on 2006-08-02
If your internet is connected, run these commands
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo dpkg-reconfigure xserver-xorg
```

---

