---
title: "Control Center Missing"
date: 2007-09-11
forum: General Help
---

### Post by measekite on 2007-09-11
I have 2 related issues.

ISSUE 1

Control Center was lost from System>Preferences.

When: rt click on System and choosing edit-menus the choice for Control Center (usually there) is no longer available.  I did find control center in the file manager and added it to the panel but I want it in the menu like it was before.

ISSUE 2

When I right click on System and choose edit-menus the button for help is grayed out so no help is available.   How do I fix this.

It seems to take a lot to really bring down Linux but it also takes alot to get back to square one when you make a mistake.  It seems more difficult to Windows but it also seems to run better than Wndows.

---

### Post by oldos2er on 2007-09-11
Go to System, Preferences, Main Menu, and you should be able to add your control center back. I don't know enough to help with the other problem, sorry.

---

### Post by measekite on 2007-09-11
I Solved the problem.

[COLOR=Red]There were 2 issues:[/COLOR]

1. Control Center was not in Main Menu

2. Main Menu was corrupted.  When doing an Edit Menu the Dialog was missing all of the buttons on the right side including adding an item and moving an item up and down.

[COLOR=Red]What Failed[/COLOR]

Reinstalling Gnome and Reconfiguring

[COLOR=Red]**What Worked**[/COLOR]
[I]
Not sure if all of these steps are necessary but I did them.[/I]

Open a terminal session and type:

sudo apt-get update

*At this point you need to type your password*

sudo apt-get -f install

I do not know what the -f is yet

sudo apt-get install ubuntu-desktop

This is some info on it

**The Ubuntu desktop system **
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

Now the fun:

Main menu came back like it should but was still missing Control Center.  So I added it back into main menu and changed the icon so what it should be.
[COLOR=Red]
Analysis:[/COLOR]

Somehow something got messed up and a generic dialog came up when you did an edit menu.  There also appears to a bug in the original install since Control Center appears once unchecked and twice when you check one of them.

[COLOR=Black]**Conclusion:**

Gnome needs some work.  You should be able to edit the entire menu system graphically.  I heard that you can with KDE but I want to stick with Gnome until I get my feet wet and then I will decide.  Things are much more difficult in Linux as opposed to Windows.  And they are much more time consuming but I have 20 years of experience with Windows doing Tech Support for a time and Dot net development also.

I hope this experience helps others who have had similar problems.  I think the solution could be used to solve other issues as well.
[/COLOR]

---

