---
title: "[SOLVED] Flashing Panels on Thin Clients - Edubuntu 7.10 Gutsy Fresh Install"
date: 2008-03-01
forum: General Help
---

### Post by batonac on 2008-03-01
I just ran a fresh install of Edubuntu 7.10 Gutsy from the server installation CD.  My server has two network cards (first one hooked to the internet, second one hooked to the thin clients) so it is perfect for Edubuntu.  I ran the setup with all the defaults, and when I finished... whoala!  The thin clients booted over the network perfectly!  They display the LDM login screen, and when I enter my username and password, they login successfully.

Now for the problems...  the desktop on the thin clients only displays itself for a few seconds.  It is the default Edubuntu desktop, except for the fact that the icons on the panels are the default gnome icons, not the Ubuntu Human ones, and the panels are dark grey and harsh looking (GTK-unthemed look)  After a few moments, the panels start to change to the Ubuntu Human GTK Theme, and the Ubuntu Human Icons, but right at that moment they start flashing.  They flash on and off (not the icons and everything, just grey strips at the top and bottom of the screen) for a few seconds, and then disappear.  I am left with a edubuntu background and a mouse pointer.  If I right-click on the mouse, I get a desktop menu, but the icons on the menu are the gnome icons, not the ubuntu icons.  The menu itself then behaves as the panels did (flashing and disappearing), If I click on a menu item quickly (like change desktop background) the resulting window also displays itself but then flashes and disappears.

When I log on to the server, I don't experience any of these problems.  Compiz fusion is enabled on the server, so I thought that the problems on the thin clients might be resulting from compiz fusion trying to run on the thin clients unsuccessfully.  I uninstalled compiz using synaptic, but then when I log on to the server (after compiz fusion is uninstalled)  it gives me a desktop without any window manager (it doesn't even fall back on metacity!!!!)  If i run metacity from a terminal, then everything works, but that is the stupidest thing yet (I have to install over 30 accounts on this system, I can't program them all to start metacity manually when gnome starts)

I'll try to get more information on this problem, I know I should probably write more information on how the system responds in many different scenarios, but I'm writing this from my house, and the server I'm setting up is at my school.  If you have any suggestions, please help me, I'll try to get any information you might want up as soon as possible.  The teachers and students at this school are dying for the computers to be back up and running again.  This was supposed to be a fast deployment, but it's not going so smooth.  I could switch to kubuntu gutsy, cause I know that that works, but I'm trying edubuntu because of kubuntu sound and printing issues.

---

### Post by batonac on 2008-03-04
I just installed fiesty and everything works.  Sorry for the trouble.  I sure do with that somebody would fix all the problems in edubuntu gutsy.

---

