---
title: "How do I change the icon for particular file, not the file type."
date: 2017-07-06
forum: General Help
---

### Post by alexander46 on 2017-07-06
In Kubuntu i would like to change single .n64 file icons. But only accessing icons of a file type seems possible.
Is there a solution?

Greetings

---

### Post by Dennis N on 2017-07-06
If you want to change the icon of a text file, I am pretty sure you have to change the icon for all text files. Otherwise, there would have to be some database of files registering the icon of each one.

---

### Post by alexander46 on 2017-07-07
so, my panel with .n64 files having individual icons (game covers) will remain a vision?

---

### Post by CatKiller on 2017-07-07
I don't know about KDE, but in Gnome clicking on the icon in the Properties for the file *does* change the icon just for that file. Perhaps KDE does the same?

Otherwise, > **alexander46 said:**
> my panel with .n64 files having individual icons (game covers) could be easily done by putting launchers on a panel rather than the files themselves.

---

### Post by Dennis N on 2017-07-07
> **CatKiller said:**
> I don't know about KDE, but in Gnome clicking on the icon in the Properties for the file *does* change the icon just for that file. Perhaps KDE does the same? Otherwise,  could be easily done by putting launchers on a panel rather than the files themselves.

Very interesting. I verified in Gnome by changing a single .rtf file to have a libreoffice-writer icon. That worked, and all other .rtf files continued to display the file type's icon. 

But I found my icon change was not recognized when opening the same file in XFCE (even when the icon I changed to was available). It reverted to the icon for the file type. Also, in XFCE desktop, there is no option to change the icon for a file in Properties - it simply displays the icon. Don't know the facts about KDE.

How is it done in Gnome? Does Gnome record some metadata in the file itself? Or some database of files with custom icons that is checked?

---

### Post by CatKiller on 2017-07-07
> **Dennis N said:**
> How is it done in Gnome? Does Gnome record some metadata in the file itself? Or some database of files with custom icons that is checked?

I'm afraid I don't know. Gnome does keep information about files all over the place. It does keep thumbnails for media files, so it's possible that it's tied in to that in some fashion.

It might be a Nautilus thing rather than strictly a Gnome thing, too.

---

### Post by alexander46 on 2017-07-07
> [COLOR=#000000]Perhaps KDE does the same?[/COLOR]
Nope..

> [COLOR=#000000][INDENT]could be easily done by putting launchers on a panel rather than the files themselves[/INDENT]
[/COLOR]


You mean, there is something like a dummy that points to the file in a manner to open it?
Where can i find this 'launcher'?

Greetings

---

### Post by CatKiller on 2017-07-07
> **alexander46 said:**
> You mean, there is something like a dummy that points to the file in a manner to open it?
Where can i find this 'launcher'?

It's done through .desktop files. They're simply text files with the correct filename extension and header. They're used for menu entries and such. You can specify the command that gets run (in this case, your emulator with a particular file, presumably) and the icon that gets displayed and a whole bunch of other stuff. If you're curious about the details, you can read through the [freedesktop.org specification]("https://www.freedesktop.org/wiki/Specifications/desktop-entry-spec/"). .desktop files are specifically cross-platform: that's what the freedesktop organisation is for.

Per-user applications are generally stored in ~/.local/share/applications. System-wide applications are generally stored in /usr/share/applications. Copying one of those files and modifying it with a text editor to suit your needs would probably be the easiest way.

I haven't used KDE, so I don't know the best way to display a panel of specific application launchers, but I'm sure you can figure that bit out yourself now that you know the facility exists. In Gnome you can generally just drag-and-drop launchers around.

---

### Post by monkeybrain20122 on 2017-07-07
Write a script to open the file, make it executable and then make a .desktop file with whatever icon you choose pointing to the script (instead of the file itself)

---

### Post by CatKiller on 2017-07-07
No need to write a script; the Exec= line would have ```
Exec=myN64emulator /path/to/particular/N64-game-file.n64
```Obviously you'd use whatever syntax the program you're launching would use.

For example, here's my launcher for the Steam game Guns of Icarus, that I happened to include in a different post:

```
[Desktop Entry]
Name=Guns of Icarus Online
Comment=Play this game on Steam
Exec=steam steam://rungameid/209080
Icon=steam_icon_209080
Terminal=false
Type=Application
Categories=Game;ActionGame;
```

As you can see, it launches steam with the GameID passed as a parameter, using steam's own syntax. Anything that you can run from the command line you could also put into a .desktop file.

---

### Post by monkeybrain20122 on 2017-07-07
> **CatKiller said:**
> No need to write a script; the Exec= line would have ```
Exec=myN64emulator /path/to/particular/N64-game-file.n64
```Obviously you'd use whatever syntax the program you're launching would use.


I don't know what is a .n64. If it is executable then sure you are right.

---

### Post by deadflowr on 2017-07-07
> I don't know what is a .n64. If it is executable then sure you are right.
An extension for an Nintendo 64 rom file.
No need to be executable as it can only run with a proper emulator; mupen64plus being a proper emulator.

---

### Post by CatKiller on 2017-07-07
> **monkeybrain20122 said:**
> I don't know what is a .n64. If it is executable then sure you are right.

It doesn't need to be; the emulator is executable, and it's the emulator that's opening that file. Exactly the same as if it was ```
Exec=totem SomeRandomMP3File.mp3
```

Edit: Ninja'd by deadflowr :)

---

### Post by alexander46 on 2017-07-08
Inside Dolphin its possible to create new 'link to application' which has unified symbol of file type as well.
you probably ment a text file with script text.
But `plain text document' is uniform again.

---

### Post by alexander46 on 2017-07-08
[ATTACH=CONFIG]275914[/ATTACH]Inside the 'desktop' folder  i created a 'basic link to file or directory', but still i cant change the icon for only one game.

---

### Post by CatKiller on 2017-07-08
> **alexander46 said:**
> you probably ment a text file with script text.
But `plain text document' is uniform again.

No, I meant a text file with the right extension that follows the .desktop file layout, like I said. You can easily achieve that by copying and modifying an existing .desktop file, like I said.

What you're doing is... something else. I don't even know what it is that you're doing there.

---

### Post by alexander46 on 2017-07-08
[ATTACH=CONFIG]275916[/ATTACH]This i what i wrote into a text document with the extension '.desktop'.
I saved it, then opened it. When it asked whether i wanna open (editor) or execute i pressed execute.
The result was:
> The desktop entry file /home/ab90/Desktop/edf.desktop has no Type=... entry.


The file was marked with an exclamation mark.

---

### Post by CatKiller on 2017-07-08
```
The desktop entry file /home/ab90/Desktop/edf.desktop has no Type=... entry.
```

This is why I suggested copying an existing working one, so that you get the format right.

---

### Post by alexander46 on 2017-07-08
How did i get it wrong? 
You are pointing out there needs to be more of a frame, to make it run like a program?!
I will look for an existing one.

---

### Post by alexander46 on 2017-07-08
[ATTACH=CONFIG]275917[/ATTACH]here i searched for .desktop everywhere and those i found have the same exclamation mark, plus i checked chromium-browser.desktop which has too many lines about chromium(?!)...

Isnt there a template?

---

### Post by deadflowr on 2017-07-08
.desktop files require 3 things in all of them
Name Exec and Type
There are basically two Types: Link and Application, and Link is rarely ever used.

Example
```
[Desktop Entry]
Name=foo
Exec=bar
Type=Application
```

Once you have those 3 entries everything else is, strictly speaking, optional.

---

### Post by alexander46 on 2017-07-08
now i found this. The .desktop file asked me then i it should open or execute, pressed execute and it informed me once more, it would start the defined execute file. then the animation (bouncing icon) started but the application did not get started. (changed the exec and icon line)
Name=FooCorp Painter Pro
	Exec=foocorp-painter-pro
	Icon=foocorp-painter-pro
	Type=Application
	Categories=GTK;GNOME;Utility;

---

### Post by alexander46 on 2017-07-08
Ah ok, you already replied.

---

### Post by alexander46 on 2017-07-08
Got the format right now, but to execute simply fails, some bouncing of the chosen icon and then nothing.

---

### Post by deadflowr on 2017-07-08
Going back to the exclamation marks, are the .desktop files marked for executable?
(usually right click on the file lists a properties option where you can set the execute bit)

EDIT:
> Got the format right now, but to execute simply fails, some bouncing of the chosen icon and then nothing.
what is the Exec= line you have?

---

### Post by alexander46 on 2017-07-08
Exec=Exec=Mupen64Plus /home/ab90/Games/N64/Mystical Ninja 2.n64
was the line [CENTER][COLOR=#000000]:mrgreen:
NOW its really correct 
[/COLOR][/CENTER] 
> [Desktop Entry]
Name=Mystical Ninja 2
Exec=Mupen64Plus /home/ab90/Games/N64/Mystical Ninja 2.n64
Icon=/home/ab90/Pictures/GameIcons/292579754aef62bf4679af7d96119f14.png
Type=Application


BUT now m getting this:
 [CENTER][COLOR=#000000]

[/COLOR][/CENTER]> KDEInit could not launch 'Mupen64Plus':
Could not open library 'libkdeinit5_Mupen64Plus'.
Cannot load library libkdeinit5_Mupen64Plus: (libkdeinit5_Mupen64Plus: cannot open shared object file: No such file or directory)


---

### Post by deadflowr on 2017-07-08
Correct command should be
mupen64plus < all small letters

Also I see spaces in the game name
Mystical Ninja 2.n64
Linux does not handle spaces well, so you will need to encapsulate those
like
```
Exec=mupen64plus "/home/ab90/Games/N64/Mystical Ninja 2.n64"
```
see the quotes.
Otherwise the system would try to run a game called Mystical...

---

### Post by alexander46 on 2017-07-08
Successfull! Thank you very very much! :))) ->Its working now *thumbs-up* <-

---

### Post by deadflowr on 2017-07-08
Hope you beat the game.
If you feel confident that the problem(s) have been solved, feel free to [mark this thread as solved.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by alexander46 on 2017-07-08
Solved![ATTACH=CONFIG]275918[/ATTACH]

---

### Post by CatKiller on 2017-07-08
Awesome. Glad to hear it. Nice one.

---

