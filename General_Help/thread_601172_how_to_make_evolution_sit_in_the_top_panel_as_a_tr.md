---
title: "how to make evolution sit in the top panel as a tray icon?"
date: 2007-11-02
forum: General Help
---

### Post by ogwilson on 2007-11-02
I want the Evolution program to be open all the time, notifying me of emails as they come, but I can't find any way to make it sit in the top panel as an icon. and I don't want it to be selectable on the bottom taskbar. Sort of like Thunderbird for Windows after using the Minimize-To-Tray plugin.

Are there any programs that offer this sort of function? Or is there some sort of way to do it within evolution?

For now, all I do is keep it open in the rightermost workspace, but i would really like for it to functon as i described.

---

### Post by Christmas on 2007-11-03
I think you can use the "alltray" application.
```
sudo apt-get install alltray
```
And then run "alltray evolution". There is also 'kdocker', but I don't know if it works with GNOME panels.

---

### Post by ogwilson on 2007-11-03
Thanks alot man, works just like i was hoping it would!

Also, can this be used for any program as well? Like I could do alltray firefox?

oh and one more. do i have to do alltray [program name] everytime i sign in or can this be automated

---

### Post by Christmas on 2007-11-03
Yes you can use it with any program. It can be automated by putting it as an autostart command. I don't remember where is in GNOME, but look in the menus, somewhere should be either autostart settings or login programs or something.

---

### Post by zoetrope666 on 2007-11-05
I just tried following this process but nothing has come up in my system tray. Indeed, I'm getting a prompt saying that I don't have a system tray..

> admin@AGREENWOOD:~$ alltray evolution

Alltray: no system tray/notification area found.
I will wait..... I have time....

In the meantime you may add a system tray applet
to the panel.


Anyone know what's going on and how i might fix this?

Any ideas would be much appreciated!

---

### Post by zoetrope666 on 2007-11-05
Ok, found a solution...

Right-clicked on panel and clicked on 'add to panel'.

In the search box I typed in 'notification area'.

Dragged icon in to panel and suddenly the evolution mail icon appeared!

Yay! FINALLY!!

Thanks guys.

---

