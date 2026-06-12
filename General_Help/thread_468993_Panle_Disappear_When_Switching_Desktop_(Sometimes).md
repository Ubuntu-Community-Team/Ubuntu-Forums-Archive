---
title: "Panle Disappear When Switching Desktop (Sometimes)"
date: 2007-06-09
forum: General Help
---

### Post by mikecon on 2007-06-09
I have had a look around the forums and searched but I'm not sure any of the posts I read were the same problem, so I thought I'd ask...

Sometimes, and only sometimes, when I switch desktops the top an bottom panels disappear (the ones that are in place when you first install Ubuntu). I can't think of anything consistent that has happened just before, or actions I have taken that might suggest a root cause, it seems quite random at the moment. But once they're gone the only thing I've been able to do is re-boot or run everything via Alt+F2.

One post I read suggested restarting the panels with something like 'x4fce panels' from a terminal started via Alt+F2, which I will try next time but it doesn't explain why they are disappearing in the first place or if there is anything I can do to stop it happening.

Also, and this may not be related, sometimes when I close an application or a window via the 'X' button the window greys slightly but stays in place and the only way of getting rid of it is to right click on the application or window 'button' in the bottom panel and choose 'Close'. After that things mostly work normally.

Thanks for any help, advice, suggestions.

Mike

---

### Post by whistlerspa on 2007-06-10
My bottom panel has disappeared today.  the xfce4 command has not restored it. i can't get it back it seems  - where did it go to?

---

### Post by mikecon on 2007-06-11
I have made some progress, but I don't think it is fixed permanently yet.

Typing xfce4-panel in a terminal window told me that it wasn't installed. This seemed odd since what advice there is says to restart xfce4 via xfce4-panel (and if xfce4-panel isn't installed then what is powering the panels when you first boot up?). However, in experimental mode I installed it (sudo apt-get install xfce4-panel) and of course I could start an xfce4 panel (which looks quite different to the standard Ubuntu panels) and eventually I added an item to that panel that allowed me to get back to Workspace 1 (I think a maximised Firefox window caused the xfce4 panel to show Firefox windows on other Workspaces. So back on Workspace 1, lo and behold the original panels are still working fine, but they are missing from all 3 other Workspaces.

So, I assume the Ubuntu panels are not provided via xfce4?
This is intermittent, sometimes I can go for hours without an issue, merrily switching workspaces with standard panels available on all of them, other times they just disappear as soon as I select a Workspace other than #1, although occasionally I can switch a few times before they disappear.

There are plenty of comments (and even an xfce4 bug report) of disappearing panels but I haven't yet found an explanation nor fix - anyone know something I don't?

*(Oh yes, and I have corrected the title of the thread, at least for this post - spelling disaster really !!)*

**Edit**
Ok, so it's gnome-panel. There's only ever been 1 bug according to:
[https://launchpad.net/ubuntu/feisty/+sources/gnome-panel/+gethelp](https://launchpad.net/ubuntu/feisty/+sources/gnome-panel/+gethelp)
which is where the panel itself links you to via right click + Get Help Online
**/Edit**

Thanks,
Mike

---

### Post by mikecon on 2007-06-13
Update

Having read some more, once I'd discovered it was gnome-panel, I tried the suggested > killall gnome-panel from one of the desktops that had lost the panels.

So, situation is panels visible on desktop 1 but mssing on the other three.
Change to desktop 2 and use Alt F2 to get a terminal window running
Type killall gnome-panel

The panels immediately reappear on desktop 2. Great I thought, it must have stopped gnome-panel, then recognised it wasn't running and automatically restarted it.

But oh no, switch back to desktop 1 and the panels are missing.
This is repeatable on any desktop where the panels are missing.
Using killall just starts them on the current desktop but removes them from whichever desktop they were visible on previously.

1) Why does killall seem not stop gnome-panel? It just seesm to move the visible panels from one desktop to another
2) I still have no idea why they disappear on all but one desktop

Any comments, hints?

Thanks,
Mike

---

### Post by stanga on 2007-06-20
same here the only  way i found to get the workspaces working again is to disable the desktop effects and re-enable them again...

anyone solved the problem?

---

### Post by Baul on 2007-07-04
Hi there

Yelp - I have been getting the disappearing panel bug as well - increasingly more so recently though.  I'm not sure if it is a side effect of using compiz but if I increase my workspaces the panels just go - forcing me to either restart the Xserver or Alt+F2 / Ctrl+arrow as mentioned above.  This never seem an issue before having to do a re-install of Fiesty.  Is it something that has sneaked in as part of a downloaded update???

Puzzled 

Baul

---

### Post by Specter043 on 2007-07-06
Same thing just started happening to me.

---

### Post by Anzan on 2007-07-16
> **stanga said:**
> same here the only  way i found to get the workspaces working again is to disable the desktop effects and re-enable them again...

anyone solved the problem?

I tried this and now I've only one workspace.

Help, please?

I'm just using Desktop Effects. On a previous install I used Compiz-Beryl but have found I'm pretty happy with the wobbly windows and the cube to switch workplaces.

---

### Post by Anzan on 2007-07-16
Me again.

Okay, it's all fine now.

My fix is to futz about with the settings and restart a few times. Not efficient, but it worked.

---

