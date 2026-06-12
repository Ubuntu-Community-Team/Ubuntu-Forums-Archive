---
title: "Hiding panels completely in Gnome"
date: 2008-07-08
forum: General Help
---

### Post by nkessler2000 on 2008-07-08
I have put a panel with quicklaunch icons on the left side of my screen. I set it to autohide so it only appears on mouse over, but part of the bar still sticks out. I changed the height in gconf-editor, but even if I set the bar height to 0, you can still see a little of the bar stick out. Also, if set to 0, the bar doesn't appear on mouse over. 

All of this likewise for the top panel which I also set to autohide.
See pic

[IMG]http://img61.imageshack.us/img61/4712/29177709hy6.jpg[/IMG]

The grey top and the bottom of the panel stick out especially. I set the transparency to 100%, but it doesn't affect the tabs at the ends. 

is there any way to hide the panels completely, so that they're completely invisible until mouse over?

---

### Post by Car60n on 2008-07-08
you can try show hide buttons and hide the panel

---

### Post by nkessler2000 on 2008-07-08
> **Car60n said:**
> you can try show hide buttons and hide the panel

yes, I could, but that's not a very good solution. I like the mouse over, not having to click a button. And also it wouldn't solve the problem of the button sticking out since you can still see the button when you click hide. I want the panel to be completely invisible until I move my mouse over it

---

### Post by Car60n on 2008-07-08
the problem is if you cannot see the panel a little then you can't move your mouse over it and if you can't move your mouse your it then you can't access the panel...

or so i think...

---

### Post by nkessler2000 on 2008-07-08
> **Car60n said:**
> the problem is if you cannot see the panel a little then you can't move your mouse over it and if you can't move your mouse your it then you can't access the panel...

or so i think...

well that seems to be the case with Gnome Panels, but other programs (awn for example) do not have this problem. I was hoping there was a workaround

---

### Post by Truedream on 2008-07-08
what about setting the opacity to 0?

---

### Post by nkessler2000 on 2008-07-08
> **Truedream said:**
> what about setting the opacity to 0?

like I said in my original post, I did that, and it makes the bar invisible, but you can still see the icons stick out, and you can still see the grey tabs at the end of the bar

---

### Post by sayakb on 2008-07-09
Goto System->Preferences->Session->Current Session and set the **Style  **for gnome-panel to *Trash*. Don't close the Session Preferences window. At a terminal, do:
```
killall gnome-panel
```
Now at the session preferences window, click **Session Options **tab and **check **the "Automatically remember..." checkbox and restart X.

---

### Post by nkessler2000 on 2008-07-09
> **LinuxIsInnovation said:**
> Goto System->Preferences->Session->Current Session and set the **Style  **for gnome-panel to *Trash*. Don't close the Session Preferences window. At a terminal, do:
```
killall gnome-panel
```
Now at the session preferences window, click **Session Options **tab and **check **the "Automatically remember..." checkbox and restart X.

I don't want to remove the panels completely, I just want them to be completely invisible on the desktop until moving the cursor over their location. 

I'm guessing now that GNOME simply doesn't have that feature. Oh well

---

### Post by hackerseraph on 2008-07-09
yeah ive spent time playing around with it before and to no avail but um what emerald theme are you using there its nice and smooth looking ^^

---

### Post by jerome1232 on 2008-07-09
I used gimp to make a transparent .png file that was 1280x24 pixels , and set it as the background for the panel, this makes it invisible for me using metacity as my window manager (other ones add shadows, can probably take them off didn't feel like trying).

---

