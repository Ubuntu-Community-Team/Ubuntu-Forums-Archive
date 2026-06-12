---
title: "Multiple desktops"
date: 2007-11-01
forum: General Help
---

### Post by gezzabob on 2007-11-01
Hi all,

Sorry but I am being a bit thick here, I recently upgraded to Gusty and playing around with it as you would normally do managed to setup 2 desktops to startup and cannot remember how to change it back.

What I mean is I have setup another desktop on a virtual terminal eg when you pres Ctrl + Alt +F1 you get a virtual terminal and when you press Ctrl + Alt + F7 you get back to the desktop but now I also have a desktop on Ctrl + Alt + F9.  I used one of the options in the menus added a second desktop left it for a while messed about with other stuff rebooted and now cannot remember what option it was to disable the second desktop.  I have tried to search through the forum but cannot seem to track down anything that will point me in the right direction.

Can anybody tell me what the option I will need to look at to enable / disable multiple desktops access from the F keys.

I hope this makes sense.

Regards Geoff.

---

### Post by bodhi.zazen on 2007-11-01
Not sure what you may have done exactly, but I hope these two links will help :

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

[http://humanreadable.nfshost.com/howtos/x_keyboard_assignments.htm](http://humanreadable.nfshost.com/howtos/x_keyboard_assignments.htm)

---

### Post by gezzabob on 2007-11-04
> **gezzabob said:**
> Hi all,

Sorry but I am being a bit thick here, I recently upgraded to Gusty and playing around with it as you would normally do managed to setup 2 desktops to startup and cannot remember how to change it back.

What I mean is I have setup another desktop on a virtual terminal eg when you pres Ctrl + Alt +F1 you get a virtual terminal and when you press Ctrl + Alt + F7 you get back to the desktop but now I also have a desktop on Ctrl + Alt + F9.  I used one of the options in the menus added a second desktop left it for a while messed about with other stuff rebooted and now cannot remember what option it was to disable the second desktop.  I have tried to search through the forum but cannot seem to track down anything that will point me in the right direction.

Can anybody tell me what the option I will need to look at to enable / disable multiple desktops access from the F keys.

I hope this makes sense.

Regards Geoff.

Have found the option that I was looking for it under : System > Administration > Login  Login Preferences > Security > Configure X Server.

In there you have the the options to start servers on the extra VT's etc ....

That is what I had used the first time to create the extra xserver/desktop and couldn't remember what the option was that I used.

---

