---
title: "[SOLVED] trying to make a shortcut..."
date: 2008-02-18
forum: General Help
---

### Post by psfelgate on 2008-02-18
Hi, this is probably a stupid question, but I am trying to make a shortcut to wvdial on my desktop to dial my modem. Now if I open a terminal and just type "wvdial" <enter> it works 100% and the terminal remains open and when I'm finished using the internet I open that same terminal where wvdial is busy running and I hit ctrl-c to disconnect.

What I've tried to do is right-click on desktop and say "create a launcher" and I put in the command wvdial.

When I double click the shortcut it works - but it runs in the background. I dont want it to run in the background because then I have to go to the running processes and end it, witch is annoying.

Is it possible to make the shortcut open an actual terminal and run wvdial in there as if I did it myself?

---

### Post by tango_ninja on 2008-02-18
where is your program located? use

```
whereis wvdial
```

I'm trying to think of a way to run a launcher in terminal.... as a work around, you could always use the **ps x** and **kill** commands in terminal afterward instead of opening up processes..

---

### Post by psfelgate on 2008-02-18
I am not sure where it is located. I can run wvdial from any folder in the terminal though. So the only problem is stopping it from running in the background when using the launcher on the desktop.

---

### Post by chavanak on 2008-02-18
wvdial: /usr/bin/wvdial 
/etc/wvdial.conf
 /usr/share/man/man1/wvdial.1.gz

Here is the location of wvdial. The second one is the config file as you can see

---

### Post by erginemr on 2008-02-18
Maybe right-clicking your top panel and two adding custom launchers, one for starting wvdial and one for stopping it will do the trick.

To achieve this, you need to right-click on one of your panels (preferably the one where your main menu resides), select add to panel, then click on the button that says create custom launcher.

This way, make two custom launchers one with "wvdial", the other with "killall wvdial". Give them appropriate names, say "Start Internet Connection" and "Stop Internet Connection", find two appropriate icons (/usr/share/app-install/icons is a good place to start, but I have used /usr/share/icons/gnome/scalable/actions for the attached screenshots) for the launchers and enjoy using them.

---

### Post by erginemr on 2008-02-18
Alternatively, you can use Gnome run dialog (Alt+F2) to start and stop your dial-up connection:
* Alt-F2 -> wvdial
* Alt-F2 -> killall wvdial

---

### Post by psfelgate on 2008-02-18
> **erginemr said:**
> Maybe right-clicking your top panel and two adding custom launchers, one for starting wvdial and one for stopping it will do the trick.

To achieve this, you need to right-click on one of your panels (preferably the one where your main menu resides), select add to panel, then click on the button that says create custom launcher.

This way, make two custom launchers one with "wvdial", the other with "killall wvdial". Give them appropriate names, say "Start Internet Connection" and "Stop Internet Connection", find two appropriate icons (/usr/share/app-install/icons is a good place to start, but I have used /usr/share/icons/gnome/scalable/actions for the attached screenshots) for the launchers and enjoy using them.

Thanks, I will give this a go when I get back home. So far it sounds like the best solution where I dont have to follow as many steps as before.

BTW is there any way to measure the amount of data sent / recieved on that connection like windows does? wvdial does not show me how much data is being sent and recieved, only shows my ip address and dns address etc.

---

### Post by erginemr on 2008-02-18
The "network monitor" applet might be the answer you are looking for...

---

### Post by psfelgate on 2008-02-19
Thanks, I will give it a go. btw the two shortcuts with "wvdial" and "killall wvdial" works! Thanks again!

I also found out last night that if I create a launcher for wvdial and select "application in terminal" then it does exactly what I was looking for. However having the two shortcuts is still easier.

---

### Post by erginemr on 2008-02-19
Great news! Have fun then! :popcorn:

---

