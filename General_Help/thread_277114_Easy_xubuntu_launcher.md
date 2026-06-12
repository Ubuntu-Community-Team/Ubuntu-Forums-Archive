---
title: "Easy xubuntu launcher"
date: 2006-10-14
forum: General Help
---

### Post by JonahRowley on 2006-10-14
Is there an easy way to create an xubuntu launcher?  I add a launcher from my panel, then I have to figure out what the command is, then manually go and give it a meaningful icon.  Can't I just take menu items and make them launchers?

---

### Post by danielph on 2006-10-20
I am interested in this also. I was looking at the ./config/xfce4, but I didn't figure it out.

bump

---

### Post by gargoyle on 2006-10-20
First off I am new to this Ubuntu stuff so take my advise with a grain of salt.

I need to create a icon for a program and what I found out was that you need the complete path to the exact probram you want to run.
In my case it looked like this:
**wine /home/ed17/.wine/drive_c/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe**

So locate the program and write the path to include everything from the beginning to the end. I went into Nautilus and looked up where the program was and wrote the path by looking at how it was display in the top of the window.

Example it show the following directory path:
[LIST]
[*]/home
[*]/ed17
[*].wine
[*]/drive_c
[*]/program files
[*]/dvdshrink
[*]dvdshrink 3.2 exe
[/LIST]

See how it goes through each directory.

Hope this helps. As I said I am new to this and if you already new this I did not know it one way or another.

Good Luck

PS. Watch out for spaces in names the are a problem.

---

### Post by danielph on 2006-10-21
The other way that you may find easier is to create icons on your desktop and drag them into Program Launcher. For this I am assuming that you have at least one item on  the desktop and a panel ready to add launcher items.

1. Right Click a desktop icon
2. Choose Desktop, Create Launcher
3. Type in the first part of the application name you want to add - it should automatically find it or give you a list. Selecting from the list will then fill all the details in including the icon if available. Now press Create
4. Right click panel, Add new item, Launcher, Add and now drag the desktop icon you created into the space under new icon. 

After this you can add as many as you like under one launcher or create more. 

This is not as easy as Gnome and I am guessing there is an easier way, but that is how I did it.

The end result for me was a set of icons at the bottom of the screen to open applications, some with menus (Bluefish can also open cssed and gftp as I use these 3 apps together, for example) and icon box at the top showing just the icons of open apps.

There are of course many icons still dotted over the desktop that need clearing up. 

The layout was inspired by Dreamlinux

 See screenshoot attached.

---

### Post by danielph on 2006-10-22
In a quest to make this easier I found that you can drag the desktop icons are already there for you at /usr/share/applications.

You can drag these straight into Program Launcher. Simple!

I am guessing that there will be more work done on Panels and Menu Editing in XFCE to make it more like what we have in Gnome. I remember Gnome not having good menu editing a few releases back.

---

### Post by derekge on 2008-04-12
Thanks to Danielph - this really helped me.  I just back tracked and saw where the command to start terminal was /usr/bin/xfce4-terminal and added it to the launcher.

---

### Post by ozarkman on 2008-06-07
Sorry about opening an old thread but I had to say thanks. I'm a new Xubuntu user. I was having problems configuring launchers and this thread solved my problem.

---

