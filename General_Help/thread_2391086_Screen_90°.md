---
title: "Screen 90°"
date: 2018-05-05
forum: General Help
---

### Post by ricardomiguelmadureira on 2018-05-05
Hello, I'm new to Ubuntu and i have a Asus T100ha, the screen is rotated 90° and the way I managed to fix it is to run xrandr -o left, but I have to run it every single time, is there any way to make that command auto run on boot or something? Thanks for your help.

---

### Post by monkeybrain20122 on 2018-05-05
Maybe it autorotates [https://ask.fedoraproject.org/en/question/98455/stop-screen-auto-rotate/](https://ask.fedoraproject.org/en/question/98455/stop-screen-auto-rotate/)


I remember my Fedora 26 with gs used to be upside down.

---

### Post by #&amp;thj^% on 2018-05-05
You can create the following file:

/etc/X11/Xsession.d/45custom_xrandr-settings and place this line into it:
```

xrandr -o left
```
I use nano here:
```
sudo nano /etc/X11/Xsession.d/45custom_xrandr-settings
```
now add your code to it:
```

xrandr -o left
```
Now exit nano with keys "ctrl+x" and type Y to save and close.

---

### Post by ricardomiguelmadureira on 2018-05-05
> **monkeybrain20122 said:**
> Maybe it autorotates [https://ask.fedoraproject.org/en/question/98455/stop-screen-auto-rotate/](https://ask.fedoraproject.org/en/question/98455/stop-screen-auto-rotate/)


I remember my Fedora 26 with gs used to be upside down.

I have my screen rotation locked and even when the Ubuntu loading screen appears it's already 90°...

---

### Post by ricardomiguelmadureira on 2018-05-05
> **1fallen said:**
> You can create the following file:

/etc/X11/Xsession.d/45custom_xrandr-settings and place this line into it:
```

xrandr -o left
```
I use nano here:
```
sudo nano /etc/X11/Xsession.d/45custom_xrandr-settings
```
now add your code to it:
```

xrandr -o left
```
Now exit nano with keys "ctrl+x" and type Y to save and close.

Didn't work...

---

### Post by #&amp;thj^% on 2018-05-05
Hmmm? and you say your code works from the terminal right?
Maybe this could be mucking it up then?
> I have my screen rotation locked 

---

### Post by ricardomiguelmadureira on 2018-05-05
> **1fallen said:**
> Hmmm? and you say your code works from the terminal right?
Maybe this could be mucking it up then?

Isn't there any other way to change the default screen orientation?
Before Ubuntu I had windows and every time I formatted the PC this problem would happen as well...

---

### Post by #&amp;thj^% on 2018-05-05
well you can remove the custom xrandr-settings then.
and try this Create the file ~/.xprofile in your Home/user directory
and add your code there:
"xrandr -o left" 
Just use your default text editor for this.
BTW I have to leave for about an hour for an event I'm entered in I'll be back to check in. But I'm running out of tricks here so fingers crossed on this one.

---

### Post by ricardomiguelmadureira on 2018-05-05
> **1fallen said:**
> well you can remove the custom xrandr-settings then.
and try this Create the file ~/.xprofile in your Home/user directory
and add your code there:
"xrandr -o left" 
Just use your default text editor for this.
BTW I have to leave for about an hour for an event I'm entered in I'll be back to check in. But I'm running out of tricks here so fingers crossed on this one.

I managed to fix it by installing lxde somehow... But on the login screen it is still 90°.

---

### Post by #&amp;thj^% on 2018-05-05
> **ricardomiguelmadureira said:**
> I managed to fix it by installing lxde somehow... But on the login screen it is still 90°.
Hey Great News! for the desktop at least! as for the login screen I have no fix for that outside of tilting your Head to see it properly. :D
Best Regards

---

