---
title: "control center"
date: 2007-07-23
forum: General Help
---

### Post by AJS302 on 2007-07-23
hi,
i recently discovered the control center in ubuntu, i can get to it by typing gnome-control-center into the terminal but i was wondering if there was a way to make it appear under the systems drop down menu instead of preferences and adminastration.
thanks,
Alexander

---

### Post by benx009 on 2007-07-23
the following instructions are for feisty, i don't know if they'll work for earlier versions of ubuntu:

go to **System -> Prefences -> Main Menu**.  Go all the way down to **System** in the "Menus" column and check "**Control Center**"

---

### Post by benx009 on 2007-07-23
If you don't see "Control Center" as an option, click on the **New Item** button in the "Main Menu" window, and copy and paste the following into the window that comes up:

**Control Center** (as the launcher's name)
**gnome-control-center** (as the command)
**Ubuntu's Control Center** (as the comment, though really, you can make that whatever you want)

Make sure the "Type" of the new launcher is "Application" (should be already set to that)
Now click on the "No icon" button and paste the following over /usr/share/pixmaps: /usr/share/icons/Human/48x48/categories/gnome-control-center.png

that should give you the default gnome-control-center icon, but you can change it to something else if you don't like it.
Click on "OK" to close the window and you should see the control center icon under the System menu.  If you don't, see if logging out and logging back in again does the trick.

You can pretty much use these instructions to launch other programs in Ubuntu, even ones that you install from outside sources (just make sure you know the **command** to run the program as that's really the only thing that matters)

---

### Post by AJS302 on 2007-07-23
i did exactly as you said but for some reason it didn't appear to work

---

### Post by AJS302 on 2007-07-23
its ok now i;ve made it work:)
thanks

---

