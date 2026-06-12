---
title: "Xubuntu 14.04: Remove volume indicator and config Firefox window"
date: 2014-12-16
forum: General Help
---

### Post by nigel-antonio-pg on 2014-12-16
Good day. I have a couple of questions that may be simple but I have spent hours trying to figure how to answer.
First of all I want to get rid of this pop up that appears every time I change the volume:

[IMG]http://i62.tinypic.com/2gxfksm.png[/IMG]

Second. I want to get rid of this part of the firefox window:

[IMG]http://i62.tinypic.com/x4lkax.png[/IMG]

That's all. I would like to do it just for cosmetic reasons and to save a little space on the monitor.
 Thanks in advance for your help.

---

### Post by vasa1 on 2014-12-16
> **nigel-antonio-pg said:**
> ...
Second. I want to get rid of this part of the firefox window:
...I suspect you'll need to do that through your window manager settings. Do you see something like **Un/Decorate** when you press **Alt+spacebar**?

---

### Post by slickymaster on 2014-12-16
> **nigel-antonio-pg said:**
> Good day. I have a couple of questions that may be simple but I have spent hours trying to figure how to answer.
First of all I want to get rid of this pop up that appears every time I change the volume:

[IMG]http://i62.tinypic.com/2gxfksm.png[/IMG]

<---snip--->

You can use dconf editor to configure it. Just set the parameter **show-notify-osd-on-scrol** value to false. See below:
[ATTACH=CONFIG]258623[/ATTACH]

After which, you will need to either logout and back in again or remove and re-add the Indicator Plugin from the panel.

---

### Post by ajgreeny on 2014-12-16
For the firefox view you can take a look at the add-on "Hide Caption Titlebar Plus" to get it to look like this on my Xubuntu-14.04.

You can configure it to look different, but you will have to play around with it to get exactly what you like.

---

### Post by nigel-antonio-pg on 2014-12-16
> **vasa1 said:**
> I suspect you'll need to do that through your window manager settings. Do you see something like **Un/Decorate** when you press **Alt+spacebar**?

Well, I'm afraid that did not work. You see, the only options that Alt+spacebar show me are these:

[IMG]http://i58.tinypic.com/11qituf.png[/IMG]

And none of them do what I want.
But thank you for your reply.

> **slickymaster said:**
> You can use dconf editor to configure it. Just set the parameter **show-notify-osd-on-scrol** value to false.
After which, you will need to either logout and back in again or remove and re-add the Indicator Plugin from the panel.

That is strange. By default the value is set to false, but the indicator still appears:

[IMG]http://i62.tinypic.com/24uvu6h.png[/IMG]

And setting the value to true din not change it. I tried to change the value and log out, change the value and restart and the result was the same.
But thanks to you I learned about this helpful tool. It has helped me to do many other things that I find useful.

> **ajgreeny said:**
> For the firefox view you can take a look at the add-on "Hide Caption Titlebar Plus" to get it to look like this on my Xubuntu-14.04.

You can configure it to look different, but you will have to play around with it to get exactly what you like.

Thank you, ajgreeny this solved the the firefox window problem. =)

I'm still looking for a solution to the volume indicator.
Thank you everyone for your help.

---

### Post by Toz on 2014-12-16
xfce4-volumed displays that notification. If you kill the process, the notifications shouldn't appear any more. Unfortunately, you'll also lose the ability to manage the volume using the media keys. xfce4-volumed doesn't appear to allow you to the ability to toggle the display of the notifications - its all or nothing. You'll need to assign volume control commands to new key combinations if you want to control volume that way.

---

### Post by vasa1 on 2014-12-16
> **nigel-antonio-pg said:**
> Well, I'm afraid that did not work. You see, the only options that Alt+spacebar show me are these:

[IMG]http://i58.tinypic.com/11qituf.png[/IMG]

And none of them do what I want.
But thank you for your reply.
...
Glad you solved the Firefox issue with ajgreeny's help. On my system which has Openbox as the window manager, I can use what I described:

---

### Post by nigel-antonio-pg on 2014-12-17
> **vasa1 said:**
> Glad you solved the Firefox issue with ajgreeny's  help. On my system which has Openbox as the window manager, I can use  what I described:

I will check openbox, it sounds handy.

> **Toz said:**
> xfce4-volumed displays that notification. If you kill the process, the notifications shouldn't appear any more. Unfortunately, you'll also lose the ability to manage the volume using the media keys. xfce4-volumed doesn't appear to allow you to the ability to toggle the display of the notifications - its all or nothing. You'll need to assign volume control commands to new key combinations if you want to control volume that way.

That works for me because my keyboard does not have volume keys, so I don't need xfce4-volumed. I didn't kill it, I took it off the application autostar list, and that solved the problem. No more OSD from the volume.
Thank you for your help, Toz.

Also, while I was looking for a solution, I found a way to configure xfce4-notifyd, the one in charge of the OSD, just type in the terminal:

```
xfce4-notifyd-config
```

Maybe that's useful for someone else.

Thank you, everyone for your help, I will mark this thread as solved.

---

### Post by vasa1 on 2014-12-17
> **nigel-antonio-pg said:**
> ...

Also, while I was looking for a solution, I found a way to configure xfce4-notifyd, the one in charge of the OSD, just type in the terminal:

```
xfce4-notifyd-config
```
...
There should be something like *Notifications* in your settings (or preferences) panel. The corresponding .desktop file is */usr/share/applications/xfce4-notifyd-config.desktop*. If you want to have even more control over how the OSD looks, there should be a gtkrc file in */usr/share/themes/theme_name/xfce-notify-4.0/* or an equivalent in *~/.themes/theme_name/xfce-notify-4.0/* if that's where your active theme is located.

---

### Post by nigel-antonio-pg on 2014-12-18
> **vasa1 said:**
> There should be something like *Notifications* in your settings (or preferences) panel. The corresponding .desktop file is */usr/share/applications/xfce4-notifyd-config.desktop*. If you want to have even more control over how the OSD looks, there should be a gtkrc file in */usr/share/themes/theme_name/xfce-notify-4.0/* or an equivalent in *~/.themes/theme_name/xfce-notify-4.0/* if that's where your active theme is located.

Hahahaha you're right! In the settings you can find the same option to configure the notifications, and I didn't noticed it until now. XD
I'm such a noob.
Thanks for the info. For now I don't think I will mess with those gtkrc files. But it is useful to know where to find them.

---

