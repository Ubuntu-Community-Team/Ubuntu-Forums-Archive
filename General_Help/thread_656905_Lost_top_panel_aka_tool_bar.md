---
title: "Lost top panel aka tool bar"
date: 2008-01-03
forum: General Help
---

### Post by X_X_loaded_X_X on 2008-01-03
Im new to ubuntu i was trying to set everything up and closed the top tool bar/ panel I cant seem to find any where how to turn it back on. I am using 7.10 ubuntu studio if it makes any difference 

thanks in advance

---

### Post by wjp.reg on 2008-01-03
right-click your mouse on an existing panel and select "new panel", then populate with the menu, etc., by right-clicking on the new panel and selecting "Add to panel.."

---

### Post by Sukarn on 2008-01-03
Right click on the bottom panel, click on **New Panel**.
Drag the new panel to the top of the screen.
Right click on it and click **add to panel** and add stuff you want to add to the panel such as **Menu Bar**, quit button, etc.

**EDIT:**
This bring up a question I had thought of earlier but never asked.
How do you go about creating a panel if someone deleted all your panels?

---

### Post by mcduck on 2008-01-03
> **Sukarn said:**
> 
This bring up a question I had thought of earlier but never asked.
How do you go about creating a panel if someone deleted all your panels?

You can't remove the last panel. As long as the gnome-panel process is running you will at least have one panel on your desktop, and by default even killing the gnome-panel process just makes it restart again.

The only way to get the last panel from your desktop is to remove gnome-panel from your Gnome session (in System/Preferences/Session) or at least change it's style to 'normal' and then kill the process.

---

### Post by notquitemichael on 2008-01-03
I remmeber pulling this off in feisty by using two monitors.
The best way to get around it is to click the desktop:
Press Alt-F1 (or Ctrl-Esc) depending on your menu short cut keys,
Then your main menu will appear,
Goto Preferences -> Main Menu [Probably]
And re-enabled the option (probably in the other section) called 'panel'
This'll load a new Gnome-Panel for you. And then you can repopulate your screen again.
(also creating a new user, creates a new desktop setup.)

---

