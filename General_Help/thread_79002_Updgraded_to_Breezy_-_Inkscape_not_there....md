---
title: "Updgraded to Breezy - Inkscape not there..."
date: 2005-10-19
forum: General Help
---

### Post by Mr. Electric Wizard on 2005-10-19
I had a backported version of Inkscape installed under Hoary and when I apt-get update with the new Breezy Repositories, I get a "Could not find icon" error.
I am also getting errors when the login screen comes up (wrong configuration error).
When I log in, when my desktop comes up it cannot find the Inkscape icon or program?
Is this because my system tried to update Inkscape with a backport that is not there anymore?
I did comment out the mirrormax lines in the Sources.list.

---

### Post by dspp on 2005-10-19
[QUOTE=Mr. Electric Wizard]I had a backported version of Inkscape installed under Hoary and when I apt-get update with the new Breezy Repositories, I get a "Could not find icon" error.
I am also getting errors when the login screen comes up (wrong configuration error).
When I log in, when my desktop comes up it cannot find the Inkscape icon or program?
Is this because my system tried to update Inkscape with a backport that is not there anymore?
I did comment out the mirrormax lines in the Sources.list.[/QUOTE]

Does the program run or is it just the icon problem? If the program is not running, try removing and reinstalling. Inkscape is available via Synaptic through the usual repositories. I installed it that way and it is working.

---

### Post by kperkins on 2005-10-19
The update uninstalls Inkscape, and you have to go into synaptic to re install it. (I think there must be conflicts with the old, backported version.)
I had that login error, too, and I (think) I had to go into the login screen setup (under System > Administration) and, in the General tab, change Local to Themed Greeter.

---

### Post by CurlyChris on 2005-10-19
I had the backported version installed too.  For some reason, when upgrading from Hoary, Inkscape is removed. :confused:  

I noticed that Inkscape was marked for removal in the megalist of package changes before I hit the ok button.  Actually, I cancelled the upgrade when I saw that, then reselected all upgraded packages and it was selected for removal again!  So I just went ahead and upgraded anyway...

But then a more up-to-date version is available in the Applications > Add/Remove Programs menu (tho I haven't actually got round to installing it yet.....).

Wierd!

---

### Post by Mr. Electric Wizard on 2005-10-19
Muchos Gracias Guys...  I knew you all could help me out!
Thanks!:)

---

