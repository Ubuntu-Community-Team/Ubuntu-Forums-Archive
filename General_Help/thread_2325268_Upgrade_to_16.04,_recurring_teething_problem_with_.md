---
title: "Upgrade to 16.04, recurring teething problem with Samba/cifs"
date: 2016-05-20
forum: General Help
---

### Post by timc4 on 2016-05-20
I've been using Lubuntu for a number of years now - I use it on a couple of PCs that I use as servers more than desktops, but I still want to be able to use them AS Desktops.  I like Lubuntu because it is lightweight, does NOT have Unity, but still allows the breadth of Ubuntu APT packages.  And it runs on "older" hardware.  Yes it takes a little work to add the packages for "server" services, and yes I am comfortable using CLI commands, but I actually prefer using a GUI for most of everyday tasks, not always having to resort to a CLI.  Well, a GUI that is not Unity anyway.

In that vein - my servers are configured to run Samba, which always function fine as servers.  Browsing my network with Windows, IOS, and Android Apps, sees all of the shared files and printers.  However, literally every time there is a version change in Ubuntu/Lubuntu, the ability to browse, from Lubuntu, using the Desktop file manager, always stops working.  This has been consistent with every upgrade from 14.04 on.  Strangely, with enough patience, system upgrades have eventually returned the ability to browse in the Lubuntu file manager, but it's never been clear from release notes WHAT fixes the issue.  So now with the move to 16.04, it has happened yet again.  Strangely, it ALMOST works.  In the file manager, selecting "Network" finds a "Windows Network" but selecting that offers no Workgroups or domains for selection, just an empty window, with "smb:///" in the file spec window.  However, if I type directly into that file spec window with a directory specification of "smb://server-id/", it will bring up a list of shared items for that particular server.  So I can mount directories, I just cannot browse for them.  I've also installed 16.04 on a Lenovo T400 (oldy but a goody), as a desktop version, Full Samba not installed - same behavior.  A strange side issue, the samba CLI executable smbtree is also failing to provide a "tree" with 16.04, so possibly this is a problem with Samba, yet no  errors are showing up in the logs.  I know that 16.04 is using a newer version of Samba than 15.10, so, potentially it is a Samba problem, but it appears to be subtle.

So have others observed this behavior?  Is it exclusive to Lubuntu or a general "all flavors" problem?

Solutions?

There is actually a separate issue with the Lenovo laptop, if it goes to sleep.  When it is awakened, the mouse cursor becomes invisible in the GUI.  Everything else works, the pointer is simply missing, although  right-click still brings up a menu.  Hard to use a GUI with an invisible pointer.... The GUI must be restarted to correct this... this is new with 16.04.

---

### Post by martella on 2016-07-08
I've similar problems. Someone has found a solution?

---

