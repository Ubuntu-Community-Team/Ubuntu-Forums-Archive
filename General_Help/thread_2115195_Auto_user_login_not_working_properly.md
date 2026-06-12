---
title: "Auto user login not working properly"
date: 2013-02-12
forum: General Help
---

### Post by juliushibert63 on 2013-02-12
I've got Ubuntu 12.10 running headless on my internal network. I have SSH access to it but no screen attached to it any longer. 

Before taking the screen away from the machine (for use in another room now) I setup auto login for one of the user accounts through the Ubuntu GUI. However it doesn't seem to be logging in. 

I've followed a guide here to try and enable the login of a user into a GUI/Desktop by setting it up through my SSH access ([http://www.liberiangeek.net/2012/10/enable-auto-login-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/enable-auto-login-in-ubuntu-12-10-quantal-quetzal/))

But to summarise I've added these lines to /etc/lightdm/lightdm.conf

```
autologin-user=enwhat
autologin-user-timeout=0
```

I've restarted the machine but till no user has logged into a Desktop environment as to be expected.

I've also tried to use X11VNC to open a VNC connection to the login screen so I can login this way and get access to the Desktop. But I've getting a lot of failed to open display errors through both X11Vnc and a normal vncserver that creates a new screen ie. vnc4server.

Btw the reason I need to have a desktop logged in as I wan't to test out some software that only has GUI access and not terminal access (like XBMC) and for my attached HDD's to mount in /media/username/. Currently as no user is logged in they're not mounting correctly.

---

### Post by fdrake on 2013-02-12
> **juliushibert63 said:**
> I've got Ubuntu 12.10 running headless on my internal network. I have SSH access to it but no screen attached to it any longer. 

Before taking the screen away from the machine (for use in another room now) I setup auto login for one of the user accounts through the Ubuntu GUI. However it doesn't seem to be logging in. 

I've followed a guide here to try and enable the login of a user into a GUI/Desktop by setting it up through my SSH access ([http://www.liberiangeek.net/2012/10/enable-auto-login-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/enable-auto-login-in-ubuntu-12-10-quantal-quetzal/))

But to summarise I've added these lines to /etc/lightdm/lightdm.conf

```
autologin-user=enwhat
autologin-user-timeout=0
```

I've restarted the machine but till no user has logged into a Desktop environment as to be expected.

I've also tried to use X11VNC to open a VNC connection to the login screen so I can login this way and get access to the Desktop. But I've getting a lot of failed to open display errors through both X11Vnc and a normal vncserver that creates a new screen ie. vnc4server.

Btw the reason I need to have a desktop logged in as I wan't to test out some software that only has GUI access and not terminal access (like XBMC) and for my attached HDD's to mount in /media/username/. Currently as no user is logged in they're not mounting correctly.

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)  
lightdm is a displya manager :  no monitor > no X > no ligthdm.


try this instead [http://blog.shvetsov.com/2010/09/auto-login-ubuntu-user-from-cli.html](http://blog.shvetsov.com/2010/09/auto-login-ubuntu-user-from-cli.html)

---

### Post by juliushibert63 on 2013-02-12
> **fdrake said:**
> [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)  
lightdm is a displya manager :  no monitor > no X > no ligthdm.


try this instead [http://blog.shvetsov.com/2010/09/auto-login-ubuntu-user-from-cli.html](http://blog.shvetsov.com/2010/09/auto-login-ubuntu-user-from-cli.html)

Thank you frdake for your speedy reply!

So am I right in saying then that as no monitor is connected that it's not triggering a Display Manager like lightdm to load and so this isn't triggering the auto-login of my ubuntu user?

Just out of interest if I connected a display cable to the Ubunutu machine (no into a monitor though) would it trick it into triggering lightdm to load?

---

### Post by fdrake on 2013-02-12
> **juliushibert63 said:**
> 
Just out of interest if I connected a display cable to the Ubunutu machine (no into a monitor though) would it trick it into triggering lightdm to load? no because the system will call X to run and X itself will ask the monitor for cong settings. If there is no respons X will give an error or stop running at all.

 when you connected to ssh you had just the terminal or a graphical login?
also why do you need an auto login if you are using ssh?

---

### Post by juliushibert63 on 2013-02-12
> **fdrake said:**
> no because the system will call X to run and X itself will ask the monitor for cong settings. If there is no respons X will give an error or stop running at all.


That makes sense!

>  when you connected to ssh you had just the terminal or a graphical login?
also why do you need an auto login if you are using ssh?

Originally when I set the machine up and installed Ubuntu 12.10 a monitor was connected so was able to login via the GUI and setup SSH access. 

Now I've removed that screen I can can only access the machine via SSH. This is fine for most tasks but occasionally I want to VNC into the machine to test something out on the GUI (e.g. XBMC as I plan to reconnect a screen to it in a couple of weeks time). So currently my thinking was that if I could get a user to login to a desktop that would allow me to get VNC access. I've tried setting up a VNC via X11 and via vnc4server but without any such luck! But I'm guessing this is because lightdm isn't starting? 

Also as no user is logging in an attached HDD isn't mounting in the folder /media/enwhat. I need to get this happening so that a couple of scripts and programs (XBMC, sabnzbd) can access the drive.

I may doing this a very confused way so please do correct me if there's a simpler method!

---

### Post by fdrake on 2013-02-12
> **juliushibert63 said:**
> That makes sense!



Originally when I set the machine up and installed Ubuntu 12.10 a monitor was connected so was able to login via the GUI and setup SSH access. 

Now I've removed that screen I can can only access the machine via SSH. This is fine for most tasks but occasionally I want to VNC into the machine to test something out on the GUI (e.g. XBMC as I plan to reconnect a screen to it in a couple of weeks time). So currently my thinking was that if I could get a user to login to a desktop that would allow me to get VNC access. I've tried setting up a VNC via X11 and via vnc4server but without any such luck! But I'm guessing this is because lightdm isn't starting? 

Also as no user is logging in an attached HDD isn't mounting in the folder /media/enwhat. I need to get this happening so that a couple of scripts and programs (XBMC, sabnzbd) can access the drive.

I may doing this a very confused way so please do correct me if there's a simpler method!

what you could do is tunnel X over ssh. So basically you use the remote computer's screen as the monitor of X. 
[http://www.cyberciti.biz/faq/linux-unix-tunneling-xwindows-securely-over-ssh/](http://www.cyberciti.biz/faq/linux-unix-tunneling-xwindows-securely-over-ssh/)

google for "tunnel x11 over ssh". I am pretty sure that is possible.

---

### Post by juliushibert63 on 2013-02-12
> what you could do is tunnel X over ssh. So basically you use the remote computer's screen as the monitor of X. 
[http://www.cyberciti.biz/faq/linux-u...rely-over-ssh/](http://www.cyberciti.biz/faq/linux-u...rely-over-ssh/)

Sounds very promising and will give a try when I'm back at the machine later today!

Thank you for the tips fdrake.

---

