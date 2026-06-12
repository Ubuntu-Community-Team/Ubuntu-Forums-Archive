---
title: "How do I delete this program"
date: 2023-05-01
forum: General Help
---

### Post by jonfisher on 2023-05-01
See screenshot:

p.s. Anyone know what the program does?     As it won't launch.

---

### Post by jonfisher on 2023-05-01
This file is on the computer also and does nothing when launched.  How can I get rid of it too please.

---

### Post by ajgreeny on 2023-05-01
Where do you see those two program icons?

Right click on them and go to the properties tab or try opening them in your text editor which might tell you much more as will the file manager.

Looking at the uninstall nostalgia item I suspect you did something in Wine which I havent used for about 10 or more years so I'm now too rusty to help you further.

---

### Post by ajgreeny on 2023-05-01
I have now seen your very recent thread about using Wine so I'm sure that is your problem.

As I said my Wine knowledge is now zero so I'll leave you in other's hands.

---

### Post by jonfisher on 2023-05-03
> **ajgreeny said:**
> Where do you see those two program icons?

Right click on them and go to the properties tab or try opening them in your text editor which might tell you much more as will the file manager.

Looking at the uninstall nostalgia item I suspect you did something in Wine which I havent used for about 10 or more years so I'm now too rusty to help you further.


If I right click both it tells me that no details are available for this app.

I can open a text editor, but if you or someone could tell me the path with ">" symbols then maybe I can find these "nostalgia/wine" files and open them in text editor...

---

### Post by Holger_Gehrke on 2023-05-03
Program starters you see in graphical environments - whether as shortcuts on the desktop or in a menu or the application overview in gnome - are actually simple text files with the extension '.desktop'. 

Depending on how you installed the program in question there are several places where they could be. 

[LIST]
[*]Programs installed for all users through package management usually put their desktop files in /usr/share/applications/.
[*]snap packages usually put their desktop files in /var/lib/snapd/desktop/applications/.
[*]Programs installed from source will probably drop their desktop files in /usr/local/share/applications if they come with one at all.
[*]For programs installed for just one user - like wine usually does it - there is ~/.local/share/applications/. The '~/' is shell shorthand for your home directory. The leading period of '.local' means this directory will not be shown unless you specifically tell the tool you're using to show you hidden files. On the command line you can tell 'ls' to show hidden files by giving the option '-a' or '--all'. In file manager and file open dialogs the keyboard combination ctrl-h usually switches showing hidden files on and off.
[/LIST]

Holger

---

### Post by ajgreeny on 2023-05-03
I think there is a hidden folder in your home named .wine but it's so many years since I used wine that I may be wrong.

Search for it and i think I remember it contains a sub folder called ***program files*** In which you may find a nostalgia subfolder.
That subfolder could contain an uninstall script or similar by which you can remove the program.

If nostalgia is your only application installed in wine you could simply remove the .wine folder in your home or uninstall wine - problem gone!

---

### Post by jonfisher on 2023-05-03
> **Holger_Gehrke said:**
> Program starters you see in graphical environments - whether as shortcuts on the desktop or in a menu or the application overview in gnome - are actually simple text files with the extension '.desktop'. 

Depending on how you installed the program in question there are several places where they could be. 

[LIST]
[*]Programs installed for all users through package management usually put their desktop files in /usr/share/applications/. 
[*]snap packages usually put their desktop files in /var/lib/snapd/desktop/applications/. 
[*]Programs installed from source will probably drop their desktop files in /usr/local/share/applications if they come with one at all. 
[*]For programs installed for just one user - like wine usually does it - there is ~/.local/share/applications/. The '~/' is shell shorthand for your home directory. The leading period of '.local' means this directory will not be shown unless you specifically tell the tool you're using to show you hidden files. On the command line you can tell 'ls' to show hidden files by giving the option '-a' or '--all'. In file manager and file open dialogs the keyboard combination ctrl-h usually switches showing hidden files on and off. 
[/LIST]

Holger

Using your instructions, I found this (screenshot below).  Now, how do I delete it properly.  Should I drag them to trash or purge them in terminal.
If you, or someone, could give me the exact thing to type into terminal, that would be very helpful, as I'm not proficient in terminal as some.

---

### Post by jonfisher on 2023-05-03
> **ajgreeny said:**
> I think there is a hidden folder in your home named .wine but it's so many years since I used wine that I may be wrong.

Search for it and i think I remember it contains a sub folder called ***program files*** In which you may find a nostalgia subfolder.
That subfolder could contain an uninstall script or similar by which you can remove the program.

If nostalgia is your only application installed in wine you could simply remove the .wine folder in your home or uninstall wine - problem gone!

ok, I found it. 
How do I delete it properly.  Should I drag them to trash or purge them in terminal.
If you, or someone, could give me the exact thing to type into terminal,  that would be very helpful, as I'm not proficient in terminal as some. 				 			  			 			  			 				 					[IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/paperclip.png[/IMG]

---

### Post by mIk3_08 on 2023-05-04
> **jonfisher said:**
> ok, I found it. 
How do I delete it properly.  Should I drag them to trash or purge them in terminal.
If you, or someone, could give me the exact thing to type into terminal,  that would be very helpful, as I'm not proficient in terminal as some.   
Since you have decided to fully remove or delete the Files/Folders just try to high light the Files/Folder then press shift + del. Well it be working? Regards and cheers

---

### Post by Holger_Gehrke on 2023-05-04
Inside that folder 'Nostalgia' should be a .desktop file. Open that file in a text editor and look for a line starting with 'Exec=' and possibly one starting with 'Path='. The Exec-line gives the actual program to start, the Path-line - if it's there - gives the working directory from which to start the program. Let's take a look at an example
```

[Desktop Entry]
Name=No One Lives Forever[COLOR=#ff0000]
Exec=env WINEPREFIX="/home/holgeh/NOLF" wine-stable C:\\\\windows\\\\command\\\\start.exe /Unix /home/holgeh/NOLF/dosdevices/c:/users/holgeh/Start\\ Menu/Programs/NOLF/No\\ One\\ Lives\\ Forever.lnk[/COLOR]
Type=Application
StartupNotify=true
Comment=No One Lives Forever
[COLOR=#ff0000]Path=/home/holgeh/NOLF/dosdevices/c:/Games/NOLF[/COLOR]
Icon=A438_NOLF.0
StartupWMClass=nolf.exe

```
That's the desktop file PlayOnLinux created for "No One Lives Forever" on my system. I've marked the path and exec lines in red. PlayOnLinux creates an extra Prefix for each program; you can think of a prefix as a virtual Windows environment. So in this case I'd remove the folder ~/NOLF, the folder ~/local/share/applications/wine/Programs/NOLF, and the icon-file 'A438_NOLF.0' (would have to use 'locate' to find that, it's a png somewhere in ~/.local/share/icons) and that would remove that program completely. In this particular case I could save myself the trouble since PlayOnLinux offers an option to uninstall programs installed through it ... 

In simpler cases - where I wrote the desktop file myself - the exec line just reads 'EXEC=wine something.exe' and the path line gives the folder where the executable is. So I'd remove that folder, the desktop file and possibly the icon file (although those are usually just a few kilobytes and I might just leave them so I don't have to create a new one if I reinstall the program later; pulling images for icons from windows .ico files is fiddly).

Holger

---

### Post by send2 on 2023-05-04
Another option in terminal run:

```
wine uninstaller 
```
that should bring up the add/remove program GUI window where you can select the program and uninstall it.

---

