---
title: "The red icon of fail in the top panel suddenly appeared"
date: 2017-02-21
forum: General Help
---

### Post by mrdc76 on 2017-02-21
The following sign of an error appeared in the top panel of my 16.10 installation. Apparently, an indicator has failed as if something was missing. That looks like a volume bar or so, but I have the volume indicator working. I had the Systemtray Indicator ([https://github.com/GGleb/indicator-systemtray-unity#system-tray-indicator-for-unity](https://github.com/GGleb/indicator-systemtray-unity#system-tray-indicator-for-unity)), but I have uninstalled it. 

How to debug this?

---

### Post by howefield on 2017-02-21
Are you saying that the broken indicator is from the Systemtray Indicator ?

Certainly, panel icons to the left of the wireless indicator tend to be from user installed applications as far as I can tell.

How did you remove it, what command/procedure did you use ?

---

### Post by mrdc76 on 2017-02-21
I don't think it is the Systemtray Indicator. I think I used sudo apt-get purge indicator-systemtray-unity to remove the systray.

I changed the icon theme to KDE 4 and the red warning icon was replaced with the one in the screenshot. Doesn't that refer to clipboard? It still doesn't work.

---

### Post by Autodave on 2017-02-21
I have the same indicator on several of my machines, but everything works fine.

I guess that that really doesn't answer your question, but I can live with that if that is all that is wrong. :-)

---

### Post by mrdc76 on 2017-02-21
I can live with it, but it's an annoyance, particularly because it just recently appeared for no good reason.

---

### Post by howefield on 2017-02-21
> **mrdc76 said:**
> I can live with it, but it's an annoyance, particularly because it just recently appeared for no good reason.

Well there will be a good reason for it, the issue being finding out what that reason is :)

If you explain exactly how you got it in the first place, ie, what do you mean by "*changed the icon theme to KDE 4*"  and I'll try and replicate.

---

### Post by mrdc76 on 2017-02-21
> **howefield said:**
> Well there will be a good reason for it, the issue being finding out what that reason is :)

If you explain exactly how you got it in the first place, ie, what do you mean by "*changed the icon theme to KDE 4*"  and I'll try and replicate.

I used the Unity Tweak Tool to change the icon set to pin down the identity of the indicator giving the red error sign. The second screenshot shows that in the KDE icon set I get the clipboard icon instead of the red error sign. This might not mean anything, though. It is as if I have (unsuccesfully) removed an app that used to have an indicator in the top panel, but I don't remember doing that.  

How did this happen in the first place, I don't know, but the red error sign appeared two days ago. Maybe an update broke it?

---

### Post by mrdc76 on 2017-02-21
I fixed it. There was a strange app called "klipper" in my Startup applications.

---

