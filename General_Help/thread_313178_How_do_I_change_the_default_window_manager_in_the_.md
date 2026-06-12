---
title: "How do I change the default window manager in the Xsessions menu?"
date: 2006-12-05
forum: General Help
---

### Post by wgscott on 2006-12-05
I have kde, gnome and xfce4 installed.  I'm currently using kdm to enable users to choose their preferred window manager among these, but I would like the "default" choice to be xfce4.  Right now it is gnome (despite a splash screen that says Kubuntu).  I can't seem to figure out where this is defined.

---

### Post by kerry_s on 2006-12-05
> **wgscott said:**
> I have kde, gnome and xfce4 installed.  I'm currently using kdm to enable users to choose their preferred window manager among these, but I would like the "default" choice to be xfce4.  Right now it is gnome (despite a splash screen that says Kubuntu).  I can't seem to figure out where this is defined.

when you select it asks you if you want to make default

---

### Post by wgscott on 2006-12-05
Mine doesn't.

I just choose (for example) Xfce4 and log in and it just goes to that window manager.

Or do you mean when I originally installed KDE it asks?  If either of these is the case, there must be some configuration file somewhere to edit.

Part 7 of the kdm handbook says it "can be configured by the systems administrator"  :roll:

[http://docs.kde.org/development/en/kdebase/kdm/different-window-managers-with-kdm.html](http://docs.kde.org/development/en/kdebase/kdm/different-window-managers-with-kdm.html)

---

### Post by d3v1ant_0n3 on 2006-12-05
By my understanding, the default session in KDM is whatever you last booted into. In GDM, it asks when you choose a session that *isn't* the default whether you'd like to make that session default. I don't know how you permanently change the default to a particular session type in KDM, but you could always try

```
 sudo dpkg -reconfigure kdm
``` which should bring up a dialog asking which DM you'd like to use as default (KDM or GDM) and switch to GDM. This would allow you to have one session type as default. And give you a nicer login screen (IMO! NO FLAMING!)

---

### Post by wgscott on 2006-12-05
> **d3v1ant_0n3 said:**
> By my understanding, the default session in KDM is whatever you last booted into. In GDM, it asks when you choose a session that *isn't* the default whether you'd like to make that session default. I don't know how you permanently change the default to a particular session type in KDM, but you could always try

```
 sudo dpkg -reconfigure kdm
``` which should bring up a dialog asking which DM you'd like to use as default (KDM or GDM) and switch to GDM. This would allow you to have one session type as default. And give you a nicer login screen (IMO! NO FLAMING!)


Thanks.  I'll give that a try.

The thing indeed "defaults" to whatever you used last time, but there are also ...

> 
are also three “magic”:

**default**
The default session for kdm is normally KDE but can be configured by the system administrator.

**custom**
The Custom session will run the users ~/.xsession if it exists.

**failsafe**
Failsafe will run a very plain session, and is useful only for debugging purposes.


So basically I want the user who clicks the "default" option in the menu to get xfce4.

---

### Post by wgscott on 2006-12-05
> **d3v1ant_0n3 said:**
>  ```
 sudo dpkg -reconfigure kdm
``` which should bring up a dialog asking which DM you'd like to use as default (KDM or GDM) and switch to GDM. This would allow you to have one session type as default. And give you a nicer login screen (IMO! NO FLAMING!)


It turns out the command is dpkg-reconfigure (no space) and it does what you say, only, but doesn't permit you to pick what the "default" in the menu is.  (In my case the default is gnome, btw, despite using kdm).

---

### Post by d3v1ant_0n3 on 2006-12-05
I think I'm confised now- I'm not entirely sure what you want to achieve, sorry.

With your GDM at present, it shows Gnome as default (its the predefined default for GDM I believe). But if you now log into an XCFE session, it will bring up a dialog asking if you want to make that your default session. And it will then become your default session until you choose another- the dialog will come up every time you switch session types I think.

Sorry for the typo btw:p

---

### Post by wgscott on 2006-12-05
The kdm session menu presents several options.  One is called failsafe, one is kde, one is gnome, one is xfce4, and one is default.  

Oddly, default is equivalent to gnome.  

Also, when I try to switch from using kdm to gdm, and restart the X-server, I get kdm back.

Oh well, it isn't that important.

---

### Post by strabes on 2006-12-05
strange; did you install the xubuntu-desktop and kubuntu-desktop packages? that should set up everything correctly...? or did you just install xfce and kde? you can change the bootsplash if you want...[http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

---

### Post by wgscott on 2006-12-06
Yeah, I installed kubuntu-desktop on top of ubuntu-desktop and then finally xubuntu-desktop.

I think if I can get xfce to behave in a civilized manner, I am ready to ditch the others.

Somewhere you can pick what the default will be, according to the KDE instructions quoted above.  I just wish they would tell you where.

---

