---
title: "[SOLVED] Editing the Main Menu and Shortcuts"
date: 2008-06-24
forum: General Help
---

### Post by Jesdisciple on 2008-06-24
I don't want to navigate through my file system just to start an app (I'm still used to the Windows 'Start' menu); how can I add it to the Main Menu and, if I use it a whole lot, the shortcuts?  (For that matter, how can I fully edit both of those?)

And I'd also like to put shortcut overflow in a dropdown menu; is that possible?

Thanks!

---

### Post by NilsE on 2008-06-24
You have all kinds of options. Here is 3

1) You can go into System > Preferences > Main Menu and add entries to each menu. Under each menu you will see a new entry option.

2) Right click on either the panel or desktop to add a launcher.

3) Right click on a menu item to add a launcher to either the desktop or panel

---

### Post by drs305 on 2008-06-24
You can add a dropdown menu on the top panel by doing this:
Right click on the ubuntu menu icon (or System, Prefs, Main Menu) and select "Edit Menus".
Select New Menu
Select the New Menu, then add New Item(s) with your desired apps
Once you have finished adding apps to your new menu, close out the Main Menu.
Next go to the panel, right click, and select "Add to Panel"
Double-click  Application Launcher.
Find the New Menu folder you created and drag it to the panel and release.

Done. :)

---

### Post by crossedout on 2008-06-24
You can right-click the main menu and choose 'Edit Menus'.  Either choose from the list available or select 'New Item' to create your own (you will need to enter the path).

Launcher is very similar:
For desktop: right-click the desktop and select 'Create Launcher' (again you will need to enter the path).
For Panel: right-click the panel and select 'Add to Panel' and select 'Application Launcher' or 'Custom Application Launcher'.

For overflow, I'd suggest looking at the 'drawer' option.  Again, right-click the panel, select 'Add to Panel' and select the 'drawer' option.  You can organize items however you like using those.

-Xout

---

### Post by Jesdisciple on 2008-06-24
](*,) I accidentally removed the Yelp shortcut...  I managed to put it back (by checking the shortcut in *Other*, adding it from there, and unchecking the shortcut) but now it has the generic icon; where is that blue "**?**" circle image stored? :???:

---

### Post by drs305 on 2008-06-24
> **Jesdisciple said:**
> ](*,) I accidentally removed the Yelp shortcut...  I managed to put it back (by checking the shortcut in *Other*, adding it from there, and unchecking the shortcut) but now it has the generic icon; where is that blue "**?**" circle image stored? :???:

Try going to the shortcut, right click, Properites, and see if a "Revert" box shows up in the lower right. If so, just click it and it will restore the original icon.

If that doesn't work, look in: /usr/share/yelp/icons/

---

### Post by Jesdisciple on 2008-06-24
I can't revert my new shortcut to the old one because they're separate shortcuts.  And I don't find the icon in that folder...  But could you try right-clicking your own Yelp shortcut, clicking Properties, clicking the icon, and pasting the default URL?

Thanks!

---

### Post by drs305 on 2008-06-24
> **Jesdisciple said:**
> I can't revert my new icon to the old one because they're separate icons.  And I don't find the icon in that folder...  But could you try right-clicking your own Yelp shortcut, clicking Properties, clicking the icon, and pasting the default URL?

Thanks!

I think the icon you are looking for is: 
```
/usr/share/yelp/icons/yelp-icon-tip.png
```

This is a blue icon, but it's not really a question mark...

When you navigate to the icons folder, you may not see any icons at first. You have to select open, and after a short period the icons will show up.

---

### Post by Jesdisciple on 2008-06-24
The icon I'm looking for is the one used for Yelp's icon everywhere (e.g. **System > Help and Support**), but right-clicking that shortcut is the same as left-clicking it and it doesn't appear in the Edit Menus window.

EDIT: But yes I see those icons and I guess that one will work until I find the other.

---

### Post by drs305 on 2008-06-24
Here it is. Sorry for the delay:
```
/usr/share/icons/Human/48x48/apps/gnome-help.png
```

---

### Post by Jesdisciple on 2008-06-24
Yes, that's it!  Thanks a bunch, everyone!

---

### Post by clay_glenn on 2008-06-24
Hi,

I'm new here.  I just installed Ubuntu and had no problems.  Used synaptic to find and install a backgammon game (gnubg).  I have to open a terminal to start the "gnubg" program.  

I saw this thread and managed to use the System>Preferences>Main Menu to add "gnubg" to the Games menu.  But when I try to use it from the menu, the program starts to initialize for about two seconds, then just disappears.  When I start it from the terminal, it opens a graphical window and runs fine.

Is there something I should configure in the Games menu launcher entry, or do some programs just need to be run from the terminal?

Thanks,

---

### Post by drs305 on 2008-06-25
> **clay_glenn said:**
> Hi,

Is there something I should configure in the Games menu launcher entry, or do some programs just need to be run from the terminal?


I installed gnubg to see what the problem might be. When you made the shortcut on the panel or desktop, the top tab, "Type", by default says 'Application'. In this case, you have to change this to 'Application in Terminal' for this app to run properly. :)

---

### Post by clay_glenn on 2008-06-25
Bingo!  That fixed it.  Thanks to you for your extra effort in actually installing it to see the problem.

---

