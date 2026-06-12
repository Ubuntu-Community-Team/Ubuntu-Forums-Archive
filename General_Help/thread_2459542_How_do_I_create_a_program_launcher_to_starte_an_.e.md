---
title: "How do I create a program launcher to starte an .exe in WINE?"
date: 2021-03-20
forum: General Help
---

### Post by Brent_Santin on 2021-03-20
Hi, so I've just installed Lubuntu 20.04. I have several Windows applications I like to use in Lubuntu (and have successfully on older versions in the past). They will run if I do the following from a shell:
[FONT=courier new]
[/FONT][INDENT][FONT=courier new]**wine <name_of_application.exe>**[/FONT]
[/INDENT]

But I cannot figure out how to create an icon on the Lubuntu desktop to start them this way.

The Lubuntu [instructions here]("https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html") says "To create a launcher graphically you can right click on the desktop and select Create Launcher." But I have never found that to be true in Lubuntu. There is simply no option given to create a launcher when right-clicking on the desktop.

I am able to create something apparently called a "symlink" icon by dragging the .exe file to the desktop (which I understand functions like a shortcut), but clicking on that doesn't start the application in Wine (it does nothing).

Right clicking on the actual .exe or the symlink icon and looking at the file properties tells me that the file is set to open with "Mono Runtime" whatever that is.  I can set it to open with another application, but there is no option for Wine Program Loader (it isn't in the list).

Despite using Lubuntu (and mostly loving it) for the past 5 years or so, I've never really understood how to create program launchers on the desktop.

If anyone can help it would be appreciated.

Thanks.

---

### Post by waffen on 2021-03-20
Hello,

For this kind of task, I prefer create a simple Python script, maybe using a GUI with buttons, like you mention you have several win apps.

---

### Post by CatKiller on 2021-03-20
> **Brent_Santin said:**
> I am able to create something apparently called a "symlink" icon by dragging the .exe file to the desktop (which I understand functions like a shortcut), but clicking on that doesn't start the application in Wine (it does nothing). 

Not in the way that you're thinking. A symbolic link is a file that points to another file. So anything that interacts with that file (or directory) is actually interacting with a file somewhere completely different, but doesn't need to know about it. It's like a copy that doesn't use any space and is never out of sync. 

> Despite using Lubuntu (and mostly loving it) for the past 5 years or so, I've never really understood how to create program launchers on the desktop.

All the launchers, and the context menu entries, and panel widgets, are .desktop files, which are just text files that are structured in a particular way. There's a post stickied in the Gaming sub-forum that will give you all the details if you wanted to create one from scratch. It's not especially difficult.

Some desktop environments have a launcher creator for the menu, and let you drag and drop the launchers wherever you like. I haven't used Lubuntu, so I don't know what it has. 

Wine comes with .desktop files to add menu entries and things, but for some reason they aren't enabled for some releases of Wine. You enable them by copying the .desktop files from whichever examples directory they're in (which I can't remember off the top of my head) to /usr/share/applications. You'll likely find them just by looking at your system, or you can search here or elsewhere for instructions.

---

### Post by guiverc on 2021-03-20
> **Brent_Santin said:**
> 
The Lubuntu [instructions here]("https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html") says "To create a launcher graphically you can right click on the desktop and select Create Launcher." But I have never found that to be true in Lubuntu. There is simply no option given to create a launcher when right-clicking on the desktop.


It works fine for me, but you'll note the manual matches the latest *stable* release, which is currently Lubuntu 20.10.   At the top left of the page, you'll note it says "Lubuntu Manual" with a book icon below that, and the release of the manual you're viewing below that (ie. 20.10).

Yes we (*Lubuntu*) hoped to have it so users could select which manual (ie. release) they are viewing as an option (*prior to the release of focal or 20.04*), but that work has not yet been completed, so all users are seeing the version that relates to the latest *stable* release (currently 20.10).

That is why you aren't seeing all options mentioned in the manual; you're using an older version of LXQt that doesn't contain them.

FYI:  and of likely no use to you, I did a QA-test install of *hirsute* a couple of days ago on a much older system (*no format of $HOME or the user directory*), and the system automatically created *wine* menu entry on the main menu & submenu with various wine programs I didn't even know I had installed (*programs I've not run in maybe 4+ years*).

---

### Post by grahammechanical on 2021-03-20
I used Wine for just one Windows application. I installed it in Wine. The process is similar to how an application is installed in Windows. Use Wine File Explorer to find the setup exe and click to install. In my case the Windows application put its own icon on the Desktop. This is in Ubuntu with Gnome.

So, I ask have you used Wine to install these Windows applications?

Regards

---

### Post by guiverc on 2021-03-20
I create a desktop launcher on using my *hirsute* system, calling it blah.

What it created (i entered the values you'll see here, ie. blah, featherpad etc)

```
guiverc@d960-ubu2:~/Desktop$   cat blah.desktop 
[Desktop Entry]
Name=blah
GenericName=featherpad launcher
Comment=blah
Exec=featherpad
Type=Application
Icon=application-x-desktop
Terminal=false
```

So that's all the "**Create Launcher**" option does.   I currently don't have a *focal* system running, nor time to explore further (*at the moment*), but hopefully that'll be a start  (the .desktop file may vary on the options you provide; I only answer blah & featherpad.

---

### Post by Dennis N on 2021-03-21
> But I cannot figure out how to create an icon on the Lubuntu desktop to start them this way
Create a .desktop file for the application in your Desktop folder. This will cause the program icon to appear on the Desktop. Right-click on the icon, and check the box "Trust this executable". Double-click to launch. The Desktop file actually doesn't need to be executable. 

Here is an example of a .desktop file for a program running under Wine. The quotes are necessary because of the spaces in the path.
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Across Lite
Comment=Play Crossword Puzzles
Exec=wine /home/dmn/.wine/drive_c/"Program Files/Litsoft/Across Lite/ACROSSL.EXE"
Icon=/home/dmn/.icons/acl3.png
Path=/home/dmn/.wine/drive_c/"Program Files/Litsoft/Across Lite/"
Categories=Game;
Terminal=false
StartupNotify=false

```

---

### Post by Brent_Santin on 2021-03-22
> **grahammechanical said:**
> I used Wine for just one Windows application. I installed it in Wine. The process is similar to how an application is installed in Windows. Use Wine File Explorer to find the setup exe and click to install. In my case the Windows application put its own icon on the Desktop. This is in Ubuntu with Gnome.

So, I ask have you used Wine to install these Windows applications?

Regards

The Windows applications that have their own installer have "installed"  fine, and created their own icon from which I can start the application.
However,  the ones I am having problems starting are Windows executables that run  on their own and do not come with, nor require an installer. For those I  can only start them using the command link, but would like to create a  launcher icon so I can start them from the desktop GUI.

---

### Post by Brent_Santin on 2021-03-22
> **Dennis N said:**
> Create a .desktop file for the application in your Desktop folder. This will cause the program icon to appear on the Desktop. Right-click on the icon, and check the box "Trust this executable". Double-click to launch. The Desktop file actually doesn't need to be executable. 

Here is an example of a .desktop file for a program running under Wine. The quotes are necessary because of the spaces in the path.
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Across Lite
Comment=Play Crossword Puzzles
**Exec=wine /home/dmn/.wine/drive_c/"Program Files/Litsoft/Across Lite/ACROSSL.EXE"**
Icon=/home/dmn/.icons/acl3.png
**Path=/home/dmn/.wine/drive_c/"Program Files/Litsoft/Across Lite/"**
Categories=Game;
Terminal=false
StartupNotify=false

```

Hi Dennis N. 

What's the difference between the lines for Exec and Path in the above?  Why two lines for what is seemingly pointing to the same location?

---

### Post by CatKiller on 2021-03-22
> **Brent_Santin said:**
> What's the difference between the lines for Exec and Path in the above?  Why two lines for what is seemingly pointing to the same location?

[https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/)

> **Exec**: Program to execute, possibly with arguments. See the Exec key for details on how this key works. The Exec key is required if DBusActivatable is not set to true. Even if DBusActivatable is true, Exec should be specified for compatibility with implementations that do not understand DBusActivatable.

**Path**: If entry is of type Application, the working directory to run the program in. 

---

### Post by Brent_Santin on 2021-03-22
Okay, using Dennis_N's example I was able to create a desktop file (program launcher) for my application. It works! Only catch is it is a blank icon on my desktop (an empty space with the icon's name beneath it). Reading online, I understand I can add the "icon=" parameter to the desktop entry.
Buy where do I store the icon bitmap (or find it) to use?

The windows application I'm trying to start under wine is an Amiga emulator (WInUAE) and I'd like to make a nice icon that looks like the Amiga logo (or something). I don't know where to store that icon graphic so the "icon=" parameter knows where to look for it.

Thanks.

(PS: I know linux has its own native Amiga emulator FS-UAE).

---

### Post by CatKiller on 2021-03-23
> **Brent_Santin said:**
> Only catch is it is a blank icon on my desktop (an empty space with the icon's name beneath it). Reading online, I understand I can add the "icon=" parameter to the desktop entry.
Buy where do I store the icon bitmap (or find it) to use?
Read the sticky in the Gaming sub-forum.

---

### Post by Dennis N on 2021-03-23
> I don't know where to store that icon graphic so the "icon=" parameter knows where to look for it.
I think the location is up to you. What is important in the Icon= line is to use the full path (starting from / ) to the icon.

---

### Post by CatKiller on 2021-03-23
> **Dennis N said:**
> I think the location is up to you. What is important in the Icon= line is to use the full path (starting from / ) to the icon.

You don't need to use the full path.

You **can** use the full path, or you can put the icon where it will be picked up by the themeing system, in which case you don't need the path or the extension, it will just work automatically with the name. And pick up a theme-specific icon if it exists.

Gee, if only there were an easy-to-follow guide that explained how to do this. But however would you find such a thing?

---

### Post by Dennis N on 2021-03-23
> **CatKiller said:**
> You don't need to use the full path.

You **can** use the full path, or you can put the icon where it will be picked up by the themeing system, in which case you don't need the path or the extension, it will just work automatically with the name. And pick up a theme-specific icon if it exists.

Gee, if only there were an easy-to-follow guide that explained how to do this. But however would you find such a thing?

A couple of comments:

For this particular program (Across Lite), I knew there was no existing icon in my icon theme. So I made the icon myself (with Inkscape). Using a full path makes it work with any icon theme, even if I change my icon theme, or if the theme is upgraded. 

Also, If you put your new custom icon in an icon theme's folder, it may be lost by an upgrade to the icon theme.

---

### Post by CatKiller on 2021-03-23
> **Dennis N said:**
> Also, If you put your new custom icon in an icon theme's folder, it may be lost by an upgrade to the icon theme.

Hicolor is the fallback for all themes. It doesn't get upgraded. The user's own hicolor won't get changed even if it did, and is higher priority than the system's hicolor. A different icon would only be used if the user's chosen theme provided one that fits better with the theme, which is generally what everyone would want.

---

### Post by ActionParsnip on 2021-03-23
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=7991](https://appdb.winehq.org/objectManager.php?sClass=application&iId=7991)

Try and get the 1.2 version :)

---

### Post by Dennis N on 2021-03-23
I would say just make a full path to the customized icon you create and you can forget about it after that.

---

### Post by Dennis N on 2021-03-23
> **ActionParsnip said:**
> [https://appdb.winehq.org/objectManager.php?sClass=application&iId=7991](https://appdb.winehq.org/objectManager.php?sClass=application&iId=7991)

Try and get the 1.2 version :)

That's it. Newspapers years ago used to publish these puzzles with their online newspapers, and you could download the puzzles for the player. I used it in Windows XP before switching to Linux in 2007. But I don't know of any now that use them. The Across Lite puzzles were way too easy for most crossword fans.

---

### Post by Brent_Santin on 2021-03-23
Thanks everyone. This thread and the sticky in the Games & Entertainment section helped me to finally understand how to create a desktop launcher!

---

