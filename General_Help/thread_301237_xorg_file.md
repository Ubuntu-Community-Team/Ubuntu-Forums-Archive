---
title: "xorg file"
date: 2006-11-16
forum: General Help
---

### Post by Magiczero on 2006-11-16
Hi

I'm trying to edit my xorg file so my monitor will run at the right resalution and when i try i get this:

> tanner@tanner-desktop:~$  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
Password:
tanner@tanner-desktop:~$ sudo gedit /etc/X11/xorg.conf
tanner@tanner-desktop:~$ gksudo gedit /etc/X11/xorg.conf

(gedit:11773): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
tanner@tanner-desktop:~$ 



my monitor is running at 1280 x 1024 but the native is 1024 x 768.  Can anybody help?

---

### Post by Derspankster on 2006-11-16
Try this:

sudo dpkg-reconfigure xserver-xorg

After backing is up you should be able to change your resolution of your monitor.

---

### Post by Magiczero on 2006-11-16
i get this:

Ubuntu Configuration                                                            
                                                                                
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; You should choose this option if you would like to attempt to autodetect  &#9474;  
 &#9474; the recommended X server and driver module for your video card.  If the   &#9474;  
 &#9474; autodetection fails, you will be asked to specify the desired X server    &#9474;  
 &#9474; and/or driver module.  If it succeeds, further configuration questions    &#9474;  
 &#9474; about your video hardware will be pre-answered.                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you would rather select the X server and driver module yourself, do    &#9474;  
 &#9474; not choose this option.  You will not be asked to select the X server if  &#9474;  
 &#9474; there is only one available.                                              &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Attempt to autodetect video hardware?                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by CowzRule on 2006-11-16
Try it this way```
sudo gedit /etc/X11/xorg.conf
```If you need help on what to edit in that file, just post it here and someone will help you.

---

### Post by CatKiller on 2006-11-17
> **CowzRule said:**
> Try it this way```
sudo gedit /etc/X11/xorg.conf
```If you need help on what to edit in that file, just post it here and someone will help you.

Don't do it that way: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Either use ```
sudo **nano** /etc/X11/xorg.conf
```

or use gksudo gedit and ignore the error message. That particular one doesn't matter.

---

