---
title: "No window bars with Compiz and XGL"
date: 2006-07-28
forum: General Help
---

### Post by blaha on 2006-07-28
I have installed XGL and Compiz. I did exactly what the ubuntu wiki told me. I use the script alternative to start Compiz since I am using KDE. But when I run the script that starts the window-decorator and compiz, the only thing that happens is that all the top window bars are lost, so I can't move or close any windows.

Is it possible to make Compiz work with KDE and Nvidia?

---

### Post by hanzomon4 on 2006-07-29
Could you post the script that you're using.
I have had a problem like this before.. Also check this place out    [compiz.net]("http://www.compiz.net/")

---

### Post by jimmygoon on 2006-07-29
If you used quinns repos you probably need cgwd

---

### Post by blaha on 2006-07-29
Thanks for replying. Like I said, I did exactly as the [wiki]("https://help.ubuntu.com/community/CompositeManager/Xgl") [described]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz"). The repo I used was "deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main"

The script I am talking about is this:
```
#!/bin/bash
#killall xfwm4 #XFCE users, uncomment this line
gnome-window-decorator &
compiz --replace gconf &
xmodmap -e "keycode 22 = BackSpace Delete"
```
I have tried to change the line "gnome-window-decorator &" to "kde-window-decorator &" and "cgwd &", but they all give the same result - No Window Bars.

---

### Post by 3rdalbum on 2006-07-29
Try running each line of the script seperately in a terminal, and see if something is stopping one of the steps from working?

In order to get Compiz working on XFCE, you need to kill the XFCE window manager. Maybe, for some reason, you need to do the same for the KDE window manager, although it sounds like that is happening anyway.

---

### Post by d351GuJu on 2006-07-29
I had exactly the same problem but now it is fixed, I have learned that when you have themes setup compiz would not start or it would start but the window bars don't show up.

Make sure everything is in default setup under kcontrol > Appearances, kcontrol > Desktop > Behavior

---

### Post by joelones on 2006-07-31
d351GuJu, what do you mean 
> Make sure everything is in default setup under kcontrol > Appearances, kcontrol > Desktop > Behavior
can you be more specific?

i am having the same problem, using kde 3.5.2 and the latest compiz from quinn's. sometimes when kde starts up the top window bars are lost and  i am  unable to click anywhere on the desktop. i can logoff and login right after and the problem is gone.

i used the following guide to setup compiz for kde
[http://www.compiz.net/viewtopic.php?id=1067]("http://www.compiz.net/viewtopic.php?id=1067")

changedthe script in ~/.kde/Autostart 
```
[Desktop Entry]
Encoding=UTF-8
Exec=compiz --replace gconf & cgwd & xmodmap -e "keycode 22 = BackSpace" &
GenericName[en_US]=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-autostart-after=kdesktop

```

any help please?

---

### Post by d351GuJu on 2006-07-31
joe,

I use KDE v3.5.3 (latest), and in the beginning I followed the same guide u posted; however, I think it is better to use [this]("http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_(or_KDM)") guide instead so that you can switch between the XGL and Xorg.

I nearly spent 7-10 hours figuring out why the window bars didn't show up when I login to XGL/compiz season.  The main reason behind this is because you need to have most of the GUI settings set to default under kcontrol.

Follow this guideline:

In the terminal, enter kcontrol and go to "Appearances & Themes".

Under Style > Click Default
Under Window Decorations > Click Default

Now go to Desktop > Behavior and click default.  That's it.

Now log back in and compiz should work with window bars.

If you have any questions post here so others can follow it as well.  And if you do get it to work plz post.

L8r,

d351GuJu

---

### Post by joelones on 2006-07-31
d351GuJu, thanks for the reply,

i un-did the startup scripts from various other guides and followed the link you provided in your reply.

i made the modifications you suggested to click on defaults for the kde GUI settings:

Style > Clicked Defaults
Under Window Decorations > Clicked Defaults
Desktop > Behavior and Clicked Defaults.

i can see the windows borders now but have two problems (that i have already encountered).

1) i only see "End Current Session" instead of reboot and shutdown when i attempt to logout

2) DPMS is now not working (was working before), i believe it has something to do with the DISPLAY=:1 in the following:

```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
```

this is what i get when i issue the command
```
xset dpms force off
```

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  147 (DPMS)
  Minor opcode of failed request:  6 (DPMSForceLevel)
  Serial number of failed request:  10
  Current serial number in output stream:  12

```

forgot to mention using Xinerma for two cloned displays

thanks for the help

---

### Post by hanzomon4 on 2006-08-09
Latest compiz needs cgwd not gnome-window-decoration

---

### Post by kiev on 2007-11-19
> **blaha said:**
>  No Window Bars.We all have this problem in  kubuntu and nvidia !!! and there is no decision of this problem !!!

---

