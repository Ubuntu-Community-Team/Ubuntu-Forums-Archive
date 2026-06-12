---
title: "Annoying KDE problems"
date: 2005-10-28
forum: General Help
---

### Post by rbrugman on 2005-10-28
Sorry for the cross-post from the Kubuntu forums, but I really need to get these problems fixed, and the Ubuntu forums are by far more active.

Here are my problems:
 
1.) While all other sounds seem to work fine, sounds from IM programs don't work at all.  I tried both the standard IM program in Kubuntu as well as gaim.

2.) When I log in, the Sound mixer comes up - every time.  I am also prompted with a message saying that my kaccessrc file cannot be written and to contact my administrator.

3.) I lost my battery monitor and can't get it back. I went in to the control center and clicked "Start Battery Monitor", but it never comes back. The option on the top is also checked, but I can't get the applet back on the panel.

Other than that, I'm well on my way to a complete linux migration.

Thanks,
Robert

---

### Post by shakin on 2005-10-28
[QUOTE=rbrugman]
2.) When I log in, the Sound mixer comes up - every time.  I am also prompted with a message saying that my kaccessrc file cannot be written and to contact my administrator.
[/QUOTE]

It's probably a saved session. When you close it, make sure you quit from it in the system tray as well.

[QUOTE=rbrugman]
3.) I lost my battery monitor and can't get it back. I went in to the control center and clicked "Start Battery Monitor", but it never comes back. The option on the top is also checked, but I can't get the applet back on the panel.
[/QUOTE]

Go do KDE System Settings -> Laptops & Power. In the Laptop battery section there is a checkbox for 'Show battery monitor'. There is also a 'Start Battery Monitor' button at the bottom that you should click to start the daemon, if it's not already started.

---

### Post by rbrugman on 2005-10-28
Thanks for the quick replies.  In regards to the first problem, I have made sure that I closed the mixer completely out.  When I log out, it's no longer opened, but yet, every time when I log in, the error message appears and the mixer is right under it.


I have also tried both of the battery recommendations.  The battery monitor IS running, because it is getting updated properly, its just that the task bar one is gone, and none of the options in the Laptop and Power turn it back on.  I've even tried to load it through "sudo systemsettings".  No luck.  I'm wondering if theres a replacement applet I can install to take over since I can't get it to come back.  Also, is there the possibility that it's hidden?  Or maybe it's not called Battery in the panel and I closed it?

Thanks!

Robert

---

### Post by Heretic09 on 2005-10-28
Go to ~/.kde/share/config/ and change the owner of the file as you and not root and the group to your user's group. Had that problem on one of my boxes and that fixed it for me.

---

