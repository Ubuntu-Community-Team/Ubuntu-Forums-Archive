---
title: "New to Ubuntu, and I can't use most desktop icons"
date: 2014-06-25
forum: General Help
---

### Post by ethankschantz on 2014-06-25
When I try to add an icon to my desktop, for example Libre Office Writer, it shows up as libreoffice-writer.desktop. When I click the icon (which isn't the icon for the software, just some gray piece of paper) It tells me that the source of the file hasn't been trusted, and it may be dangerous to open the file. I'd ignore this if after that it let me open the software, but it doesn't give me the option, just the red cancel button. And when I right click it and go to properties, it won't let me go into "permissions," saying I'm "not the owner." I am on the main account, so shouldn't I be able to change that, or at least use my desktop icons?

---

### Post by Paulgirardin on 2014-06-25
Ubuntu really isn't set-up to have desktop icons,that's a Windows thing and it's messy.
You can add apps to the launcher by opening the app (search for it in the dash) and once it is open there will be an icon in the launcher,you can right click on the icon and choose "lock to launcher".
Or you can learn to search in the dash.It usually only takes 3 characters to find most apps.For example: ter will bring terminal up as first choice or wri will bring up Libre Office Writer as first choice.This works for files too,though you usually have to open a file via the file browser at least once for the search function to learn it's existence.
I open everything via the dash and only have 3 items in the launcher.

---

### Post by ethankschantz on 2014-06-25
Okay, I thought that might be the case, I was just kinda hoping it wasn't. Mainly I just wanted to find a way to make my launcher a bit more organized. Not a huge deal. Thanks!

---

### Post by grahammechanical on 2014-06-25
Think of the Dash as a slide out desktop. It never gets filled because it can be scrolled. It can be searched and filtered and it also presents recently used files and not just applications. Opened application windows do not hide the icons.

Regards.

---

### Post by deadflowr on 2014-06-25
> **ethankschantz said:**
>  And when I right click it and go to properties, it won't let me go into "permissions," saying I'm "not the owner." 

What method did you do to get the files to the desktop?

Also, +1 to simply using the launcher.

---

### Post by Bucky Ball on 2014-06-26
If you really want a more 'Window-sy' desktop environment you might want to try something other than Unity. Xfce4 is highly configurable and can have desktop icons easily, lxde is also an option.

To install either, simply look them up in Software Centre, install, logout, choose the new environment from 'Sessions', log in.

As for the warning message, don't worry about it. It happens. I created new launchers just the other day and happened everytime. Allow it. (I was then dragging the launcher to the toolbar panel and deleting the desktop icon, but same same ...)

---

### Post by Paulgirardin on 2014-06-26
I also forgot to mention that you can rearrange icons in the launcher by dragging them off the launcher and back on in a different position.
And you can launch apps by holding down the super (windows) key and the overlay number that appears on the icon after 2 seconds.

---

### Post by grumblebum2 on 2014-06-26
> **ethankschantz said:**
> When I try to add an icon to my desktop, for example Libre Office Writer, it shows up as libreoffice-writer.desktop. When I click the icon (which isn't the icon for the software, just some gray piece of paper) It tells me that the source of the file hasn't been trusted, and it may be dangerous to open the file. I'd ignore this if after that it let me open the software, but it doesn't give me the option, just the red cancel button. And when I right click it and go to properties, it won't let me go into "permissions," saying I'm "not the owner." I am on the main account, so shouldn't I be able to change that, or at least use my desktop icons?

If you really want a desktop icon you may find all you have to do is right click on the .desktop file
properties > permissions 
and tick execute.

You can copy applications launcher files from **/usr/share/applications** to your desktop.

---

