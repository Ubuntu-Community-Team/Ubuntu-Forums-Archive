---
title: "mouse double click not working suspect update as cause"
date: 2015-09-13
forum: General Help
---

### Post by ibod on 2015-09-13
Hi

 I have a remote PC accessed via vnc  running Ubuntu 14.04 

This remote PC has a "Logitech Click! Optical" Mouse (this mouse has a 'double left click' button that worked up to a day or two ago)

Now the mouse is working fine apart from the double click function (this is needed because the user is disabled and can not double click.

Currently the double click button is functioning as 'Back' ( ie when clicking on a folder to open it, you move up one level to the previous folder, instead of opening the folder you are clicking on) 

how can this best be fixed remotely, the end user can follow basic instructions offline.

---

### Post by chessnerd on 2015-09-14
This page seems relevant to your situation: [https://help.ubuntu.com/community/MouseCustomizations](https://help.ubuntu.com/community/MouseCustomizations)

It looks like most of this is editing configuration files or installing software via command line, so that should be doable remotely.

---

### Post by ibod on 2015-09-14
> **chessnerd said:**
> This page seems relevant to your situation: [https://help.ubuntu.com/community/MouseCustomizations](https://help.ubuntu.com/community/MouseCustomizations)

It looks like most of this is editing configuration files or installing software via command line, so that should be doable remotely.

Thanks Chessnerd,

This page does look very relevant to my problem, but there is no xorg.conf in /etc/X11/

I found this page [http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there) which contains the following 


> 
 The xorg.conf does not exist by default any more. You CAN create one though.
  Boot into recovery mode and select Root Shell. 
Then run:
X -configure   

Then:
cp /root/xorg.conf.new /etc/X11/xorg.conf   

Reboot and you can edit the new Xorg.conf.
     

and 

> 
There is absolutely **no** reason to reboot even once. 
Just open terminal, write 
sudo X -configure; sudo cp ... and sudo /etc/init.d/gdm restart 
(assuming Ubuntu, not KUbuntu).



When I attempt to create the xorg.conf with the second method 

```

sudo X -configure

```

I get the error 

```

Fatal server error:

Server is already active for display 0

    If this server is no longer running, remove /tmp/.X0-lock

    and start again.





Please consult the The X.Org Foundation support 

     at http://wiki.x.org

 for help. 



 ddxSigGiveUp: Closing log


```

This is where it starts to get harder remotely and beyond a disabled user 
following instructions over the phone 
I assume here I would open a tty and stop X
where I would lose the remote sesion !

```

sudo service lightdm stop

```

then 


```

X -configure

```

and restart x

```

sudo service lightdm start

```

and then copy xorg.conf to /etc/x11

and edit it in some way ???

Is there some way to create the xorg.conf without stopping X and losing the remote session ???

and what would need to be edited to reassign the mouse button correctly ???

---

### Post by chessnerd on 2015-09-14
If you need to stop X in order to create this file, then I wonder if it would be possible to create a bash script that performed all of the necessary actions for you. A script that stops X, then creates the configuration file, and then restarts the remote session. It seems like once the xorg.conf file is created you should be able to edit it without these problems.

As for how to assign the mouse button to double click, that is detailed in this section: [https://help.ubuntu.com/community/MouseCustomizations#Setting_up_double_click](https://help.ubuntu.com/community/MouseCustomizations#Setting_up_double_click)

---

