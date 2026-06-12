---
title: "Get rid of Mate plymouth screen in Ubuntu"
date: 2014-10-17
forum: General Help
---

### Post by Lockheed on 2014-10-17
I have Ubuntu 14.04, but I installed MATE according to [this guide]("http://www.omgubuntu.co.uk/2014/08/install-mate-desktop-ubuntu-14-04-lts") to check it out. I quickly decided I don't like it, so I uninstalled it according to [that guide]("http://linuxg.net/how-to-properly-installremove-mate-1-8-onfrom-ubuntu-14-04-trusty-tahr/").

The problem is, that my system is using full disk encryption, and when it boots-up, it asks for disk password still on ubuntu-MATE screen, instead of the old pure Ubuntu screen.

This is strange, because I run
```
sudo update-alternatives --config default.plymouth
```
and set it all back to the default Ubuntu logo. I even removed everythin MATE-related from /lib/plymouth/themes/

Yet it does not help.

---

### Post by CantankRus on 2014-10-17
Do you mean the greeter?
Look in** /usr/share/lightdm/lightdm.conf.d/**
When I installed the gnome-flashback session it added a file here and changed the greeter session.
My **50-unity-greeter.conf** determines the greeter with a line
```
greeter-session=unity-greeter
```

But if you have a higher numbered file with **greeter-session=[COLOR="#808080"]xxxxxx[/COLOR]** it will load that greeter.
Have a look in any higher numbered file and comment out any line that reads 
```
greeter-session=[COLOR="#808080"]xxxxxx[/COLOR]
```

eg my **60-lightdm-gtk-greeter.conf** after [COLOR="#FF0000"]commenting[/COLOR] out the  **greeter-session** line... 
```
[SeatDefaults]
[COLOR="#FF0000"]#[/COLOR]greeter-session=lightdm-gtk-greeter
```

---

### Post by Lockheed on 2014-10-17
> **CantankRus said:**
> Do you mean the greeter?
Not at all.
I mean the plymouth screen where it asks for disk password before it even begins booting.

---

### Post by CantankRus on 2014-10-17
Never used disk encryption so I have no idea then except look in the comments section of the uninstall guide link you gave.

---

### Post by Lockheed on 2014-10-17
Thanks, but I did that even before removing Mate.

---

### Post by Dennis N on 2014-10-17
> **Lockheed said:**
> ... I run
```
sudo update-alternatives --config default.plymouth
```
and set it all back to the default Ubuntu logo. I even removed everythin MATE-related from /lib/plymouth/themes/

Yet it does not help.

After you select a Plymouth theme as you are doing, you then need to run the command

```
sudo update-initramfs -u
``` 

and then reboot.

---

### Post by Lockheed on 2014-10-17
I swear I did this, but I think for another kernel. Now it worked. Thanks.

---

### Post by Dennis N on 2014-10-17
Glad you got it fixed. Thanks for the feedback.

---

