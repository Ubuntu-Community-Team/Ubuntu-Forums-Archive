---
title: "Icons are screwed up and I can't fix them. Need help badly."
date: 2008-06-12
forum: General Help
---

### Post by kaldor on 2008-06-12
My dad is an idiot to computers. I left linux running when I left to go out, I came back and find the top bar (using gnome) on the side of the screen. My dad was trying to "fix the font" and somehow that involved messing up the taskbar >.>

So after I get that fixed, the icons are jumbled up. They refuse to move. So I unchecked "lock to panel" on them, but some refuse to go back to original state. Is there any way to like, reset the taskbars to default?

Screenshot (look at top right):

[IMG]http://img2.putfile.com/main/6/16313342590.jpg[/IMG]

---

### Post by wolfen69 on 2008-06-12
could you upload a bigger pic?

---

### Post by Vivaldi Gloria on 2008-06-12
Some icons are grouped together and you can grab them on the left side and move them. You cannot move them individually. See the picture attached.

---

### Post by kaldor on 2008-06-12
The pic seems to have disappeared, can't find it >.<

But the upload icon, pidgin, and other running apps are appearing to the right of the power button, and I can't fix it.

---

### Post by Vivaldi Gloria on 2008-06-12
Those together form the notification area. just as i told u, u can move them by right clicking on the left.

or why dont u move the power to the right?

---

### Post by kaldor on 2008-06-12
Like I said, it won't move. I know how to move the icons =p

It just won't go back into place.

---

### Post by kaldor on 2008-06-12
I'm still in need of help D:

---

### Post by NilsE on 2008-06-12
You simply have one or more icons that have lock to panel checked so go through them all and make sure they are all unchecked.  Then do the moves.

Simply put, a movable icon can not move past a locked icon so they all have to be movable.  For notification areas or grouped icons you select the handle on the left and right click it for the lock option.

---

### Post by kaldor on 2008-06-12
New problem. I deleted the panel and made a new one. Now applications that are opened won't appear. I don't see my internet configs, I don't see the pidgin icon (the white icon with the green ball), and it's starting to annoy me.

What can I do to bring back the old config?

---

### Post by trevelyan on 2008-06-12
the way i move the icons is i uncheck "lock to panel" and then i right click that same icon again and click on "move". after that i just move the mouse and they follow.

i found that it gave me more control to do it this way than just trying to drag them into place. try that.

dont forget to lock them to panel again or they will screw up again next time you boot.

---

### Post by Vivaldi Gloria on 2008-06-12
You probably have the following on the right side of the panel:

1) Notification Area (upload manager, network connections etc)
2) sound icon
3) wheather + clock
4) power icon
5) any seperator lines there might be
6) any other icons you have added yourself?

Have you right click on everyone of them and uchecked lock? Have you right clicked on the left side of the notification area and uncheked lock?

Maybe you should post a screenshot so we can see what is going on.

Or how about you add a new notification area to an empty area of the panel and practice moving it around.

---

### Post by kaldor on 2008-06-12
Like I just said... the icons for network manager, pidgin (when it's running, the green circle..) and other running apps will not show up.

---

### Post by Vivaldi Gloria on 2008-06-12
> **kaldor said:**
> New problem. I deleted the panel and made a new one. Now applications that are opened won't appear. I don't see my internet configs, I don't see the pidgin icon (the white icon with the green ball), and it's starting to annoy me.

What can I do to bring back the old config?

Right click an empty area on the panel, choose add to panel, then choose notification area

---

### Post by trevelyan on 2008-06-12
> **kaldor said:**
> New problem. I deleted the panel and made a new one. Now applications that are opened won't appear. I don't see my internet configs, I don't see the pidgin icon (the white icon with the green ball), and it's starting to annoy me.

What can I do to bring back the old config?

right click the panel..
click add to panel

a window will pop up with everything you can put there..  network monitor, notification area, etc.

---

### Post by kdcoetzee on 2008-06-12
You can reset the Panel with

  1. rm -r ~/.gconf/apps/panel 
  2. Log out of GNOME (crtl-alt-backspace restart gnome)
  3. Log back in.


if you are paranoid you can make a backup first...

---

### Post by NilsE on 2008-06-12
> **kaldor said:**
> New problem. I deleted the panel and made a new one. Now applications that are opened won't appear. I don't see my internet configs, I don't see the pidgin icon (the white icon with the green ball), and it's starting to annoy me.

What can I do to bring back the old config?
Right click on panel and select "add to panel" then add back what you are missing. The one you are missing for showing running apps is window list.

---

### Post by cariboo on 2008-06-12
The best way to stop this from happening again is to give your Dad his own desktop. Just go to System-->Administration--Users and Groups and add another user, fill out the form with a password just for him. Then he can login into his own home directory where he doesn't have to share with you and vice-versa.

Jim

---

