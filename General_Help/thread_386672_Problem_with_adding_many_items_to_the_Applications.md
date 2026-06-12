---
title: "Problem with adding many items to the Applications menu"
date: 2007-03-17
forum: General Help
---

### Post by TL_CLD on 2007-03-17
Hey all,

Ok, I've been using Ubuntu now for a couple of days, and while my general feelings are positive, I do though have an issue that it bothering the heck out of me:

I need to add 18 VNC and 27 gnome-terminal entries to the Application menu. I want to do it like this:

[VNC Menu]
---> VNC Item 1
---> VNC Item 2
---> VNC Item 3
---> ...
---> VNC Item 18
[SSH Terms]
---> SSH Term 1
---> SSH Term 2
---> SSH Term 3
---> ...
---> SSH Term 27

But it just wont work. I add the items, but I can't "activate" them, so they wont show up. It's like the Menu Editor (Alacarte?) just hangs there, not really doing anything.

I've currently created all of the above as desktop launchers, but daaamn, does that look ugly or what! I would much prefer being able to create a proper menu, and then adding them to my main panel for a neat and tidy "drop-down" menu.  :)

Anybody got any good tips/tricks for this issue?

Sincerely,
Thomas

---

### Post by zvacet on 2007-03-17
If you are able to make launcher from desktop you are capable do the same in alacate.If your desktop launchers works there is no reason that one you make in alacarte doesn´t.

---

### Post by TL_CLD on 2007-03-17
> **zvacet said:**
> If you are able to make launcher from desktop you are capable do the same in alacate.If your desktop launchers works there is no reason that one you make in alacarte doesn´t.

Well, fact is Alacarte wont accept my new items. It's as if it wont write the XML to the necessary file(s). It's pretty darn weird..  :( 

Thomas

---

### Post by d_keith on 2007-03-23
I seem to recall a similar problem.  I would right-click the task bar to bring up the Gnome Edit Menus function,  select the menu to edit, then click on "New Item".  I would fill in the blanks for the new item,  click OK.... Open the menu to see the new entry, nothing!.... Once I figured out that "alacarte" was the program being run to edit the menus,  I opened a terminal window and ran it from a command line. I could then see that there was a folder permission error that I was able to correct........Hope that helps!

---

