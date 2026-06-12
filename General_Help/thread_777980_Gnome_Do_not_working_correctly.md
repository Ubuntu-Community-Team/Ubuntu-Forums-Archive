---
title: "Gnome Do not working correctly"
date: 2008-05-01
forum: General Help
---

### Post by jshbbe on 2008-05-01
Ok, so I have upgraded to 8.04 recently and I have to say that it is awesome.  I haven't booted into Windows for almost a week now.  However, I am very used to using Launchy (an app launcher in Windows) that is very similar to Gnome Do.  Gnome Do will work most of the time, but sometimes when I use the hotkey to bring it up (I have mine set to <Alt>space) it will not become visible.

I have found out that it is actually running when I use the hotkey.  I can type the program that I am looking for and hit enter and the program will launch.  However, I cannot see what I am doing because Gnome Do is not visible.  The only way to get Gnome Do visible again seems to be to open it or another program from the menus.  I'm not sure what the problem is, but some help would be appreciated.

By the way, I have Compiz disabled and am running on Metacity with compositing enabled.  I'm not sure if that has anything to do with it.

---

### Post by Bubba64 on 2008-05-01
Gnome do has to be opened each time you restart your computer from the applications or icon. I am not sure if you are shutting your computer off. There can sometimes also be a delay to bring it up. You might check to see if you have the latest version as well

---

### Post by jshbbe on 2008-05-01
Gnome do is running, and I am not shutting my computer off.  I can access Gnome Do by pressing shortcut keys, but after a while I cannot make Gnome Do visible anymore by pressing the shortcut keys.  Like I said, I can still type the program that I want to run and press enter and the program will run, but I cannot see what I am doing because Gnome do is not visible.  I have the latest version of Gnome Do installed, and I even installed the svn version thinking maybe this would help.  Both versions give me the same problem.

As an example to what I am talking about, I press Alt+space to bring up Gnome do, I don't see anything, if I type 'firefox' and press enter it will load Firefox.  It does all of this even though Gnome Do is not visible.

Thanks for your help.

---

### Post by Bubba64 on 2008-05-01
> **jshbbe said:**
> Gnome do is running, and I am not shutting my computer off.  I can access Gnome Do by pressing shortcut keys, but after a while I cannot make Gnome Do visible anymore by pressing the shortcut keys.  Like I said, I can still type the program that I want to run and press enter and the program will run, but I cannot see what I am doing because Gnome do is not visible.  I have the latest version of Gnome Do installed, and I even installed the svn version thinking maybe this would help.  Both versions give me the same problem.

As an example to what I am talking about, I press Alt+space to bring up Gnome do, I don't see anything, if I type 'firefox' and press enter it will load Firefox.  It does all of this even though Gnome Do is not visible.

Thanks for your help.

Strange, I have noticed that I can hit the keyboard prompt and input the destination and get there without seeing the Gnome do popup but if I wait it does always show up. Maybe removing it then reinstalling will fix it that is what I would do. Good Luck

---

### Post by RAOF on 2008-05-01
> **jshbbe said:**
> ...
By the way, I have Compiz disabled and am running on Metacity with compositing enabled.  I'm not sure if that has anything to do with it.

Yeah, this is a bug which only seems to appear when running under Metacity's composite manager.  If you're running AWN as well you can see that AWN will disappear in this case.

I haven't yet filed this as a bug on Launchpad.  One of us should - it's probably a Metacity bug, but filing it against Gnome Do would be a good start.

---

### Post by jshbbe on 2008-05-01
Yep, that is exactly what happens.  I'm glad somebody else has experienced this.  I'll see if I can file a bug report on it.

Thanks, for your help.

---

### Post by alexandremrj on 2008-06-09
I had also the same problem but i have it solved for now.

When you enable compositing_manager in the configuration editor for metacity you will probably have the mouse_button_modifier (4 lines below the compositing manager) as <Super>.

What happens (probably) is that Gnome-Do uses the <Super>+Space , so when you try to enable Gnome-Do with metacity compositing and press <Super> the system interprets it as the modifier for actio click and gets confused.

In my case I solved this problem changing the mouse_button_modifier to <Alt> and i now have both compositing and Gnome-Do

See if it works for you?

---

### Post by QuickBrownFox on 2008-12-21
**_Workaround_**

1. Run Gnome Do
2. Type anything
3. Press the down arrow key
3. Press escape

Gnome Do should now be visible and stay that way until you restart. Unfortunately the drop down list that appears when you press the down arrow is not visible. Hope they fix this soon. I assume it's a problem with metacity.

Note: I only have this problem while using Avant Window Navigator with metacity with compositing enabled.

---

