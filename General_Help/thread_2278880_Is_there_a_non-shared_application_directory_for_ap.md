---
title: "Is there a non-shared application directory for application menu links?"
date: 2015-05-19
forum: General Help
---

### Post by snakyjake on 2015-05-19
How do I remove a specific application link/shortcut from a specific user's or group's application menu?
For example, I don't want all users to notice or launch the VNC server from their application menu.  This should only show up for a specific user or a server admin group.

I noticed the links are stored /usr/share/applications.
Is there a non-shared application directory?

I prefer a command line solution.

Thanks in advance.
Jake

---

### Post by Dennis N on 2015-05-19
> Is there a non-shared application directory for application menu links?

Yes - ~/.local/share/applications

To have an application NOT appear in the menu:

Working in the user's account, copy the .desktop file for the application you don't want to show from /usr/share/applications to ~/.local/share/applications

Open the copy in ~/.local/share/applications in a text editor and add the line:

**Hidden=true**

Or I suppose you could put this in the global file in /usr/share/applications, and not put it in the copy in ~/.local/share/applications for any user you want to see it.

However, any user who knows about desktop files and where to find them could just remove it. Maybe there is a better way, but it doesn't come to mind right now.

Edit:

Regular users who can't use sudo could not edit or delete files in /usr/share/applications, so I think the second way is perhaps better. But still nothing stops them from copying the file to ~/.local/share/applications and then removing the line, and it will show again in the menu. But then, anyone could just run the application from the command line - you don't need the menu. Some mod to the permissions might be added?

---

