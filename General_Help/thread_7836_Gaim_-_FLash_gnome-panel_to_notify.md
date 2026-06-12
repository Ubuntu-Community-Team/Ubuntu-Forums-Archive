---
title: "Gaim - FLash gnome-panel to notify?"
date: 2004-12-11
forum: General Help
---

### Post by gwon on 2004-12-11
I don't know if it annoys anyone else that the GAIM notify plugin doesn't make the taskbar icon flash when a new message is recieved (under gnome).

I found this patch: [http://bugzilla.gnome.org/show_bug.cgi?id=120439](http://bugzilla.gnome.org/show_bug.cgi?id=120439)

But I don't know the first thing about how to use it, or if it will even work.

Anyone know of any way to get GAIM windows to flash in the gnome taskbar to notify new messages, or can help me with the above patch?

Any help appreciated.

Craig

---

### Post by Ubuntu_User on 2005-02-17
Anybody figure out how to get the taskbar to flash when new messages are received?

---

### Post by tkiesel on 2005-02-23
I'd love to see this functionality. Some visial method of notifying when the IM/chat window is on another Workspace would be great too.

---

### Post by champagnemojo on 2005-02-25
Are y'all enabling the 'Message Notification' plug-in, and then checking the option to 'Set window manager "URGENT" hint'?  These are in the GAIM preferences of course.  That works in xfce4...I figure it would work in GNOME too.  Bear in mind that in a very small number of GTK themes it won't appear to flash due to color choices.

---

### Post by tkiesel on 2005-02-25
[QUOTE=champagnemojo]Are y'all enabling the 'Message Notification' plug-in, and then checking the option to 'Set window manager "URGENT" hint'?  These are in the GAIM preferences of course.  That works in xfce4...I figure it would work in GNOME too.  Bear in mind that in a very small number of GTK themes it won't appear to flash due to color choices.[/QUOTE]

I tried that a while back, and didn't see any results with Gaim on the currently focused workspace or on another workspace.  Perhaps my theme is the problem? I'll test that at home tonight.

---

### Post by Davo on 2005-02-26
Hey, if you get it to work let us know what theme you used and what conditions the theme may have to meet for it to work. I know it used to work when I used KDE on mandrake, but have been unsuccessful with several themes for GNOME. So please let us know :)

---

### Post by bored2k on 2005-02-26
its not a solution but i made gaim hide nu messages in tray until clicked

this makes gaim tray icon flash until click, wich is a lot better than not knowing when msg'd [not all of us like annoying msg sounds]

---

### Post by tkiesel on 2005-02-26
I found a [patch](http://www.people.virginia.edu/~mse5q/blink/)  that will enable the Message Notification plugin's "URGENT" hint setting work. 

I don't know if this patch is to be applied to Metacity itself, or to the app (Gaim in this case)

I haven't the foggiest as to how to apply the dang thing, and I don't feel like hosing Gnome.  So.. if anyone here more accustomed to .patch files in Metacity knows how one might go about applying this sort of thing to Gaim in Warty, I'd be much obliged.

It's a step in the right direction for us, perhaps.

much love,
-T

---

### Post by xatm045 on 2005-03-17
Anyone get this to work?  I still can't seem to get gaim to flash across workspaces...

It's a shame...

---

### Post by mike998 on 2005-03-18
Probably unrelated but there is a plugin called "Guifications" which will give you a toaster popup type of notification - This can be set to display on a number of different type of circumstances.
There is a .deb available on the webpage:
[http://guifications.sourceforge.net/](http://guifications.sourceforge.net/)

---

### Post by tsalem on 2005-04-02
I managed to get flashing taskbar buttons in gnome by patching libwnck using the blink-state patch. I then compiled a .deb of it and installed that. I had a problem with patching it, but __J over on Linuxquestions helped me out. I hope this thread helps:

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=309073](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=309073)

---

### Post by twan on 2005-04-21
I really want this too.. It's been so annoying not having it..

Can't someone of the developer's implement this patch and update the .deb in the repositories so everyone can simply upgrade their packages ?

If not..

Following this thread: [http://www.linuxquestions.org/questions/showthread.php?s=&threadid=309073](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=309073)

Where do i need to go (wich directory) to apply the patch ?

---

### Post by syszd on 2005-04-24
Its Easy i installed in in 2 min.

1) make a folder called patches in the libwnck source folder
2) copy the file libwnck-2.8.1-blink-state.patch into the folder you just made
3) cd into the libwnck folder and run the command **sudo dpkg-buildpackage -us -uc**
4) install the .deb file with **sudo dpkg -i <package_name>**
5) then run **sudo echo libwnck-<version> hold | dpkg --set-selection**

step 5 makes it so synaptic or apt-get dosent overwrite it

**Note:** replace the values of <package_name> and <version> with the correct info.

Enjoy your flashing gaim-panel :D

---

### Post by twan on 2005-05-15
Can you be a bit more specific about that ?

the libwnck folder, do you mean "/usr/include/libwnck-1.0/libwnck" with that ?

I did what you said, and after "dpkg-buildpackage -us -uc" i get:

dpkg-parsechangelog: error: cannot open debian/changelog to find format: unknown file or directory
dpkg-buildpackage: unable to determine source package

---

### Post by zafar on 2005-06-05
click the following for hoary flashing taskbar 

[flashing taskbar!](http://ubuntuforums.org/showpost.php?p=200885&postcount=11)

---

