---
title: "Creating Command Shortcuts is ridiculously complicated"
date: 2018-09-22
forum: General Help
---

### Post by creativiii on 2018-09-22
Hello,

I want to preface this that I'm fairly new to Ubuntu and Linux in general so this might be a non issue, however as a new user this problem has really stumped me and if there is a simple solution I have yet to figure it out (which I would consider a problem itself)

The problem:
[B][SIZE=3]I want to create a desktop shortcut to an application that I know how to launch via terminal

[/SIZE][/B] Let's get meta and say I want to create a Desktop shortcut to ```
/usr/bin/gnome-desktop-item-edit
``` which is the application used to create Shortcuts. 


[LIST=1]
[*]I open my terminal
[*]Type /usr/bin/gnome-desktop-item-edit ~/Desktop/ --create-new
[*]This launches the application
[/LIST]

[IMG]https://i.imgur.com/Tbxe7fG.png[/IMG]

Looking at this it's pretty clear what I have to do, so I compile it with my information:

[IMG]https://i.imgur.com/eKQksc9.png[/IMG]

This, unfortunately does not start the program.

The workaround for this is to create an .sh file like this:

```
#!/bin/bash/usr/bin/gnome-desktop-item-edit ~/Desktop/ --create-new
```

And then, creating a .desktop shortcut pointing to that:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_GB]=gnome-desktop-item-edit
Name[en_GB]=Shortcut
Exec=/home/leonardo/Utilities/createshortcut.sh
Name=Shortcut Creator
Icon=gnome-desktop-item-edit

```

Am I doing this wrong? Is there a way to do this that doesn't force me to do double the work that should be needed?

The second problem I've found:
 [SIZE=3][B]creating "Links" to applications. 
[/B][/SIZE]
This is a great feature that technically should work just like it does in Windows.


[LIST=1]
[*]Right Click on Application
[*]Create Link
[*]Move Link wherever you want
[*]Double Click it
[*]The program starts
[/LIST]

However, here's what happens:


[LIST=1]
[*]I right click on the app
[*]I create a link
[*]I start it without moving it to another folder and it works perfectly
[*]I move it to another folder and it stops working
[/LIST]

Am I also doing this wrong? There has to be some basic knowledge I'm missing here because I just cannot wrap my head around it

Please help

---

### Post by TheFu on 2018-09-22
TL;DR  - skimming makes it seem like you want to make a link to the GNU tool that makes .desktop files.  That seems like the long way.  Linux isn't Windows.  You don't need a .pif file like Win3.1 used.
```

$ cd ~/Desktop
$ ln -s /usr/bin/gnome-desktop-item-edit   
# this is a symbolic link and can be made do any file or directory that you have permissions to see.
```

Done.  If you want all the fancy stuff, you'll need to find the ".desktop" file and link to that.  I'd use **locate** for that.

The way you are trying to do it, **is** ridiculously complicated.

BTW, this is wrong:```

#!/bin/bash/usr/bin/gnome-desktop-item-edit ~/Desktop/ --create-new
```

```
#!/bin/bash

/usr/bin/gnome-desktop-item-edit ~/Desktop/ --create-new
```
The first line needs to be alone. Having an extra blank line is common for readability.  I don't know what the 3nd line does.  I'm not a gnome user.

---

### Post by creativiii on 2018-09-22
> **TheFu said:**
> TL;DR  - skimming makes it seem like you want to make a link to the GNU tool that makes .desktop files.  That seems like the long way.  Linux isn't Windows.  You don't need a .pif file like Win3.1 used.
```

$ cd ~/Desktop
$ ln -s /usr/bin/gnome-desktop-item-edit   
# this is a symbolic link and can be made do any file or directory that you have permissions to see.
```


How do I use this? 
This still doesn't work

Running it in terminal results in a Link to the program on my desktop that gives me this error when launched

[IMG]https://i.imgur.com/zpuzPfL.png[/IMG]

What if I want to launch this from a desktop shortcut?
```
WINEPREFIX=/home/leonardo/Photoshop wine64 /home/leonardo/Photoshop/Photoshop.exe
```

I'm not sure I understand your post, as I said I know how to make Links to applications, but those don't work outside the folder they're created in

---

### Post by TheFu on 2018-09-22
Does /usr/bin/gnome-desktop-item-edit exist? 

When you put them in other directories, are the permission bits the same?  Are all the files referenced inside correct still?  For example, is the icon file in the expected place?
 
Those are all the guesses I have. Hopefully someone else will have better ideas.

---

### Post by ajgreeny on 2018-09-22
A simpler way may be to open an existing .desktop file, eg **/usr/share/applications/gedit.desktop**, in a text editor and edit the content as you want, then put it in ~/.local/share/applications with a new name.

---

### Post by creativiii on 2018-09-22
/usr/bin/gnome-desktop-item-edit does exist, but also gives me the same error as the link so I'm going to suppose the problem is that it just can't be opened like that.

I actually managed to get it to work with this
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_GB]=gnome-panel-launcher
Exec=/usr/bin/gnome-desktop-item-edit '/home/leonardo/Desktop/' --create-new
Name[en_GB]=test
Name=test
Icon=gnome-panel-launcher
```

But I would still be very grateful for any help with launching Wine applications because this still doesn't work. 

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_GB]=photoshop
Exec=WINEPREFIX=/home/leonardo/Photoshop wine64 '/home/leonardo/Photoshop/Photoshop.exe'
Name[en_GB]=Photoshop
Name=Photoshop
Icon=photoshop
```

I can start it with:


wine64 '/home/leonardo/Photoshop/Photoshop.exe'

But without the Wineprefix it's completely unusable

---

### Post by mc4man on 2018-09-22
what is the exact path to Photoshop.exe?
(if unsure locate it in the file browser, DnD the file on to an open terminal & post the printed path

---

### Post by QIII on 2018-09-22
Hello!

If you have solved the initial issue, please create a new thread for the question about Wine in the WINE sub-forum.

Thanks.

---

### Post by mc4man on 2018-09-22
Assuming path is corrent you could try
```
Exec=env WINEPREFIX="/home/leonardo/Photoshop" wine64  "/home/leonardo/Photoshop/Photoshop.exe"
```
or 
```
Exec=env WINEPREFIX="/home/leonardo/Photoshop" wine  "/home/leonardo/Photoshop/Photoshop.exe"
```

---

### Post by creativiii on 2018-09-22
> **mc4man said:**
> Assuming path is corrent you could try
```
Exec=env WINEPREFIX="/home/leonardo/Photoshop" wine64  "/home/leonardo/Photoshop/Photoshop.exe"
```
or 
```
Exec=env WINEPREFIX="/home/leonardo/Photoshop" wine  "/home/leonardo/Photoshop/Photoshop.exe"
```
This worked!

Thank you

---

### Post by creativiii on 2018-09-22
Just wondering, with filemanager-actions, is there a way I could bring up the [COLOR=#000000]gnome-desktop-item-edit but for that specific folder?

[/COLOR][IMG]https://i.imgur.com/0r6FURE.png[/IMG]

It's pretty confusing and I haven't been able to work it out myself

---

### Post by mc4man on 2018-09-22
> **creativiii said:**
> Just wondering, with filemanager-actions, is there a way I could bring up the [COLOR=#000000]gnome-desktop-item-edit but for that specific folder?
It's pretty confusing and I haven't been able to work it out myself
 Sure (if I understand you..
 Create as in screens, then open target folder, r. click on open space in that folder, the created launcher will go into target folder.
(If possibility that there is no open space (listview on fully populated folder) then _also_ enable Display item in selection.. option, then r. click on _any_ file in target directory

---

### Post by mc4man on 2018-09-22
If you want actions displayed directly in context menu then disable 'root' option in filemanager-actions Preferences menu as in screen.

---

