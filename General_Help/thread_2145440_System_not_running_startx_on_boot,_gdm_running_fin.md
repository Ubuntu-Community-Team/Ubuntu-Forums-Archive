---
title: "System not running startx on boot, gdm running fine"
date: 2013-05-15
forum: General Help
---

### Post by LordVeovis on 2013-05-15
When I boot my system it is not running startx.  I can manually run startx and it will boot, but I need it to start automatically.  I am sure this is something simple but I cannot seem to find this online.  Right now the system is set to use gdm but lightdm is installed as well and changing to lightdm does not make the system startx automatically either.

---

### Post by slickymaster on 2013-05-15
See if this can help you: [Start_X_at_Boot]("https://wiki.archlinux.org/index.php/Start_X_at_Boot")

---

### Post by LordVeovis on 2013-05-15
> **slickymaster said:**
> See if this can help you: [Start_X_at_Boot]("https://wiki.archlinux.org/index.php/Start_X_at_Boot")

I have tried this.  This is mainly reffering to having startx run after a login from the command line if I am correct.  I believe the idea here in this article is when you are not using a Display Manager, which I am.

---

### Post by steeldriver on 2013-05-15
I don't think the 'system' actually 'runs startx on boot' if you're using a display manager (lightdm / gdm)

What should happen is that the system runs (as root) the display manager, and when you login at the GUI, the DM authenticates you and then starts your chosen X session, using the scripts located at /etc/X11/Xsession and any relevant session startup files in your home dir

The 'startx' command is a way for a user to bypass all that and start a session in the absence of a display manager (e.g. with a simple window manager)

So if you have gdm / lightdm installed and want a graphical DM-based login then you need to look at why the DM is not starting - which shouldn't be anything to do with startx afaik

---

### Post by LordVeovis on 2013-05-15
> **steeldriver said:**
> I don't think the 'system' actually 'runs startx on boot' if you're using a display manager (lightdm / gdm)

What should happen is that the system runs (as root) the display manager, and when you login at the GUI, the DM authenticates you and then starts your chosen X session, using the scripts located at /etc/X11/Xsession and any relevant session startup files in your home dir

The 'startx' command is a way for a user to bypass all that and start a session in the absence of a display manager (e.g. with a simple window manager)

So if you have gdm / lightdm installed and want a graphical DM-based login then you need to look at why the DM is not starting - which shouldn't be anything to do with startx afaik

Ok, this makes sense, but I am never presented with a GUI login.  If I check services gdm is running 
```
# service gdm status
gdm start/running, process 2198
```

I have the account set to log in automatically, any thoughts?

---

### Post by LordVeovis on 2013-05-15
**Update**

If I disable automatic login I get the login screen but if I set it to auto login it will not work.

---

### Post by osirisgothra on 2013-05-15
if you think its a corrupted configuration somewhere you have the package manager reinitialize it

sudo dpkg-reconfigure gdm

or... maybe the upstart got messed up you can re-generate the upstart from the /etc/init.d/gdm using 

update-rc.d gdm defaults

im not sure if defaults is what you want, i think it starts at runlevels 1+ < 6 and stops on 0/6
or something like that, ive only done this one time and i might not be remembering all the details
of course if its really messed up you can try purging it and reinstalling it making sure you got rid
of /etc/init.d/gdm and /etc/init/gdm.conf (and the /etc/rc?.d/*gdm* links too else you might be
stop/starting it at the wrong time regardless of the other stuff though this generally wouldnt happen
afaik..        if it ends up using too much of your time and no end is in sight for some
reason you may just install a different display manager like lightdm, xdm, or whatever kids are using
these days.

hope this helps  

-o-

---

### Post by LordVeovis on 2013-05-15
I tried teh first 2 suggestions, have not tried a purge yet, however the problem occurs with both lightdm and gdm just the same.  As long as I dont have the system set to auto-login I am fine.

---

