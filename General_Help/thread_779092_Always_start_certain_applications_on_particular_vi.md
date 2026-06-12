---
title: "Always start certain applications on particular viewports with compiz"
date: 2008-05-02
forum: General Help
---

### Post by Arathon on 2008-05-02
I know that Devil's Pie exists, but I was under the impression that Compiz had a plugin that enabled similar functionality.  My desires are pretty basic; I'd like Pidgin (on startup) to put the Buddy List on the desktop 4, and I'd like Amarok and NetBeans to always start on desktop 2.  

I've searched and searched, and I've found mentions of a compiz plugin that supposedly handles this, but I can't find it.  Hopefully someone in here has some idea if this really exists, and if so, where to find it.

Thanks.

---

### Post by maphilli14 on 2008-05-02
I'd even settle for a shell script that could be started manually to place specific apps on a particular screen/face of the cube.

Mike

---

### Post by issih on 2008-05-02
This is doable I think, using the "place windows" plugin.

In ccsm (you'll need the full ccsm not just the simple one) enable the place windows plugin and go to its configuration page. Open the "Fixed Window Placement" tab, then add a new entry to the "Windows with fixed viewport" list. For simplicity I'd just use the little grabber utility to set the window class, the x position is then the face on the cube ranging from 0-3 (any other value seemed to make the window move entirely out of the viewable space and be totally inaccessible, so stick to low numbers :)

Hope that does what you are after

---

### Post by leeko on 2008-10-06
Hi,

sorry to resurrect an old thread, but I'm having a slight problem with this.

I'm running compiz, and have set the "place" plugin to open thunderbird on viewport 2, and zim on viewport 3. Both are also set to start maximized, as per the "window rules" plugin, and this works fine. Both programs are set to autostart via a script in ~/.kde4/Autostart.

Thunderbird starts on viewport 2, no problem. But, no matter what I put in the field for the zim entry, compiz ignores it and opens it on viewport 1. Here is what I have in the field at the moment:

(class=Zim) | class=zim | title=:Home - Zim | title=Zim | title=zim

Viewport is set to 3 (x), 1 (y). I have set compiz to 4 x viewports and 1 y.

I hope someone here can point me toward the solution!

Regards,

Lee

---

### Post by Halfwalker on 2008-10-14
This is along the same lines.  It seems that Thunderbird will always open every window with a title of "Mozilla Thunderbird", before it changes the title to whatever it finally ends up with.

For example, on first opening TB, you'll see the title as "Mozilla Thunderbird", and instants later it changes to "Inbox for [email]joe.blow@domain.com[/email] - Thunderbird".  Open an existing email, and it does the same thing - first with "Mozilla Thunderbird", then with the actual subject line.

Thankfully, the Compose window starts with the title "Compose:"

The reason for this complaint is that you can't use compiz window placement rules to put things where you want.  I would like to start TB at 150,100, email windows at 700,140 and compose windows at 800,350.  That lets you see the folder list on the left of the main TB window, and replies don't cover the whole original email.

But you can't.  The main TB window and email windows will always open at the same spot.  Rules like this just won't work ...

(class=Thunderbird-bin) & title=^Mozilla Thunderbird$   150  100
(title=-*Thunderbird$)                                  700  140
(title=^Compose:)                                       800  350

I was hoping to catch the main window with the first rule, and email windows with the second.  But since even email windows open with "Mozilla Thunderbird", the first rule catches them.

Is there any way to have compiz delay before looking at the title ?

D.

---

