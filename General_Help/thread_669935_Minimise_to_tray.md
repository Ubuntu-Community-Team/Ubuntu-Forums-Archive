---
title: "Minimise to tray?"
date: 2008-01-16
forum: General Help
---

### Post by Tech_Power888 on 2008-01-16
I am just having a slight problem with my fresh installation of 7.10.

Everything is working fine but when I hit "close" on my pidgin buddy list, the program completely exits, but in my old installation it would "minimise" to my top toolbar, where I would simply click once to get my buddy list back. Anyone know how I can do this again? 

I am pretty sure Amarok is the same, whereby I will hit "close" and it would normally minimise to my top tray, but now it just exits completely. I can still minimise my buddy list with pidgin (to my BOTTOM tray) but this just causes unnecessary clutter on my desktop, especially when surfing/watching tv/chatting.

Thanks in advance.

Ryan.

---

### Post by VON_CAPO on 2008-01-17
When Pidgin is running you already have the icon tray, so, click on that icon once and Pidgin will be minimized to tray, click again and it will show up.

---

### Post by Tech_Power888 on 2008-01-17
I think you missed my point, sorry.

I mean that when I "close" my buddy list, it disappears completely. No more pidgin. But it used to be set up such that I would have my little pidgin icon in the top corner of the screen when I "closed" my buddy list. I could simply click this again and it would bring back up any conversations/buddy list. This is a new installation of ubuntu now though, FYI.

Ryan.

---

### Post by VON_CAPO on 2008-01-17
What if you run pidgin from the terminal?
Does it report any error?

```
you@yourcomputer:~$ pidgin
```

---

### Post by steeleyuk on 2008-01-17
Tools > Preferences

Is 'Show system tray icon' set to 'Always'?

---

### Post by Tech_Power888 on 2008-01-17
Yes it is set to always. If I run it from the terminal, there are no errors. But it doesn't do what I want it to either. I thought it would just be a simple setting. Very strange indeed. Maybe I need to choose "add to panel" and find something in there?

Ryan.

---

### Post by Joeb454 on 2008-01-17
That is strange, if you want it out of your way you could right-click the title bar of the window and send it to another workspace maybe?

---

### Post by VON_CAPO on 2008-01-17
OK, I got a workaround.

1- Install " alltray "

2- Right click om the upper panel and select "+Add to panel", choose "Custom Application Launcher",
and input the following:

Name:   Pidgin
Command:   alltray "pidgin"
Comment:   Pidgin starting in the tray

3- Done!

---

### Post by Tech_Power888 on 2008-01-20
Sorry guys, I don't think I made myself clear enough. Capo your suggestion is good, but it's not what I am after. You can achieve the same result by simply dragging the Pidgin icon to the panel. 

What I mean is that my "buddy list" does not sit up in the top right hand corner of the panel. NORMALLY, there is a little green "buddy list" icon, and it stays up there EVEN WHEN you hit "close" on your buddy list window. But in my situation, doing this simply shuts down Pidgin altogether. Bye bye pidgin.

Same idea with Azureus. If I hit close then it SHOULD minimize to my panel, but instead it just disappears. Exits.

Ryan.

---

### Post by Raval on 2008-01-20
> **Tech_Power888 said:**
> Sorry guys, I don't think I made myself clear enough. Capo your suggestion is good, but it's not what I am after. You can achieve the same result by simply dragging the Pidgin icon to the panel. 

What I mean is that my "buddy list" does not sit up in the top right hand corner of the panel. NORMALLY, there is a little green "buddy list" icon, and it stays up there EVEN WHEN you hit "close" on your buddy list window. But in my situation, doing this simply shuts down Pidgin altogether. Bye bye pidgin.

Same idea with Azureus. If I hit close then it SHOULD minimize to my panel, but instead it just disappears. Exits.

Ryan.

I have the exact same problem.

---

### Post by stee20000 on 2008-01-27
I had this prob too...see below from UGM6R:

You have probably removed the notification area on the panel:
Right-click on the panel in a blank grey area.
Add to panel
Notification Area (in Utilities)
Add

Hopefully it should be back (somewhere) now. You can move the notification area in the panel afterwards (right-click).

---

### Post by Raval on 2008-01-28
> **stee20000 said:**
> I had this prob too...see below from UGM6R:

You have probably removed the notification area on the panel:
Right-click on the panel in a blank grey area.
Add to panel
Notification Area (in Utilities)
Add

Hopefully it should be back (somewhere) now. You can move the notification area in the panel afterwards (right-click).

This solved my issue, thanks

---

