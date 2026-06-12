---
title: "2 questions"
date: 2008-05-15
forum: General Help
---

### Post by Spacedementia87 on 2008-05-15
My first is about the Ubuntu time.

It seems to display down the bottom as an hour slow and I can't change it at all.
Even If I try to sync it or change it manually it won't change.  I have checked my bios time and it is fine.

My second is that since I have updated to Hardy one of my hard drives does not automatically mount on boot.  How do I fix this?

---

### Post by Mr A Mouse on 2008-05-15
> **Spacedementia87 said:**
> It seems to display down the bottom as an hour slow and I can't change it at all.
Even If I try to sync it or change it manually it won't change.  I have checked my bios time and it is fine.

Have you checked your time zone and Daylight Savings preferences?

> My second is that since I have updated to Hardy one of my hard drives does not automatically mount on boot.  How do I fix this?

[http://ubuntuforums.org/showthread.php?t=640951](http://ubuntuforums.org/showthread.php?t=640951)

Hope that helps! :)

---

### Post by Spacedementia87 on 2008-05-15
How do you check daylight savings options?

---

### Post by Spacedementia87 on 2008-05-16
bump...

I can't find the settings anywhere

---

### Post by Mr A Mouse on 2008-05-16
And on that, unfortunately, I can't help--I had to go back to Vista for work (eww), and my Ubuntu box is now running Server, not Desktop.

One place to check, however, is as follows:

System > Preferences > and see if there is a time or time and date preference.

---

### Post by brigux on 2008-05-16
can you please specify where you are and post the result of:
```
cat /etc/ntp.conf
```

---

### Post by ibuclaw on 2008-05-16
[LIST]
[*]Click on the Time Applet in your menu.
[*]Click the "Edit" command button.
[*]Click the "Time Settings" command button.
[*]Click the "Unlock" command button.
[*]Choose your username and type in your sudo password.
[*]Change the Time Zone to that of your Continent/Town (ie: Europe/London)
[*]Change the configuration from "Manual" to "Keep Synchronised with Internet Servers".
[/LIST]
Look at my attachment for visual help.

Regards
Iain

---

### Post by Spacedementia87 on 2008-05-16
> **tinivole said:**
> [LIST]
[*]Click on the Time Applet in your menu.
[*]Click the "Edit" command button.
[*]Click the "Time Settings" command button.
[*]Click the "Unlock" command button.
[*]Choose your username and type in your sudo password.
[*]Change the Time Zone to that of your Continent/Town (ie: Europe/London)
[*]Change the configuration from "Manual" to "Keep Synchronised with Internet Servers".
[/LIST]
Look at my attachment for visual help.

Regards
Iain

I had it on keep synchronised and I thought that was the problem so I changed it to manual and it was displaying the right time in the settings box just not in the bottom corner

---

### Post by Spacedementia87 on 2008-05-16
[IMG]http://img391.imageshack.us/img391/531/screenshotxg4.png[/IMG]

This is how I normally have it


[IMG]http://img241.imageshack.us/img241/9518/screenshot1jv0.png[/IMG]

And this is what I mean by the time being right in the settings but not on the display

---

### Post by Spacedementia87 on 2008-05-16
bump

---

