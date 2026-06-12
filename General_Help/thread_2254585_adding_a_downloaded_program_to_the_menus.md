---
title: "adding a downloaded program to the menus"
date: 2014-11-28
forum: General Help
---

### Post by meanmrmustard on 2014-11-28
I've downloaded FileZilla 3.9.0.6 due to issues with the outdated version in the Ubuntu repos but it doesn't look as if it can be installed.
The only way I see to run it is to issue ./filezilla from the FileZilla's bin directory. It currently resides in my home dir.

What do I have to do to create an entry in the application menus?
Should it/ could it be made into a .deb package?, and what about updates - will this need to be done manually?... and then re-installed when upgrading to the next LTS? I'm using Ubuntu Gnome 14.04

---

### Post by flaymond on 2014-11-28
Filezilla is supported in Ubuntu.

Type this to install Filezilla:


```
 sudo apt-get install Filezilla
```

If you wanna update, type :

```
sudo apt-get update
```


I'm using Lubuntu, and using Main Menu tool to do that. I believe Ubuntu also do have Main Menu tool. Type Main Menu in the search bar (top left).

---

### Post by Dennis N on 2014-11-28
You need to create a .desktop file for the application. This link will show how that is done:

[https://developer.gnome.org/integration-guide/stable/desktop-files.html.en](https://developer.gnome.org/integration-guide/stable/desktop-files.html.en)

Should it/ could it be made into a .deb package? 
Not necessary.

what about updates - will this need to be done manually?
Yes.

and then re-installed when upgrading to the next LTS?
Again, yes.

---

### Post by Dennis N on 2014-11-28
Here is a .desktop file made for the game machinarium:

```
[Desktop Entry]
Name=Machinarium
Comment=Play Machinarium
Exec=machinarium
Categories=Game;
Icon=/home/dmn/games/Machinarium/menu-icon-3a.png
Type=Application

```
I saved the file as **machinarium.desktop** in [B]~/.local/share/applications
[/B]
Name= is how it is named in the menu. Comment=  is the tooltip. The Exec= line has the command that starts your program. Usually you put the full path to the program executable file, but this example starts a script in ~/bin that in turn starts this program. ~/bin is one of the automatically searched locations for commands.

---

### Post by meanmrmustard on 2014-11-29
Thanks Dennis, just what I needed.

edit:
I've created the file but when I tried to save it I was unable to get to the hidden files, so I saved to my ~ dir then moved it to .local/share /applications in the file manager.
I unzipped the FZ file to my home dir, the executable lives in ~/FileZilla3/bin and is run from that dir by issuing ./filezilla.

The desktop file:
```
[Desktop Entry]
Name=Filezilla3
Comment=Run Filezilla3
Exec=~/FileZilla3/bin/filezilla
Categories=Internet;
Icon=~/FileZilla3/share/icons/hicolor/32x32/filezilla.png
Type=Application
```


It's not showing up in the menu yet.

Something isn't quit right but I'm not sure what it is.
Does the Exec line look correct? or does it need ./ in front of the executable? - or should there be slashes in front of the ~ symbol?

I used FileZilla3 as the name to differentiate it from the older version since I haven't uninstalled it yet.

---

### Post by meanmrmustard on 2014-11-29
Thanks for  the reply but apt-get only installs whatever version Ubuntu has seen fit to put in the repos, the present version is ancient.

---

### Post by monkeybrain20122 on 2014-11-29
> **meanmrmustard said:**
> Thanks Dennis, just what I needed.

edit:
I've created the file but when I tried to save it I was unable to get to the hidden files, so I saved to my ~ dir then moved it to .local/share /applications in the file manager.
I unzipped the FZ file to my home dir, the executable lives in ~/FileZilla3/bin and is run from that dir by issuing ./filezilla.

The desktop file:
```
[Desktop Entry]
Name=Filezilla3
Exec=~/FileZilla3/bin/filezilla
Categories=Internet;
Icon=~/FileZilla3/share/icons/hicolor/32x32/filezilla.png
Type=Application
```


It's not showing up in the menu yet.

Something isn't quit right but I'm not sure what it is.
Does the Exec line look correct? or does it need ./ in front of the executable? - or should there be slashes in front of the ~ symbol?

I used FileZilla3 as the name to differentiate it from the older version since I haven't uninstalled it yet.

Did you make the .desktop file executable? I am not sure about this but I think you need the full path in the Exec line, i.e Exec=/home/yourusername/FileZilla instead of ~/FileZilla

---

### Post by meanmrmustard on 2014-11-29
> **monkeybrain20122 said:**
> Did you make the .desktop file executable? I am not sure about this but I think you need the full path in the Exec line, i.e Exec=/home/yourusername/FileZilla instead of ~/FileZilla

I did forget to make it executable, thanks for that.
Also changed ~ to /home/me just in case that would make a difference.

Still I'm only getting the 3.7.3 version from the main menu instead of 3.9.0.6 which is what the .desktop file points to.

---

### Post by buzzingrobot on 2014-11-29
> **meanmrmustard said:**
> 
Still I'm only getting the 3.7.3 version from the main menu instead of 3.9.0.6 which is what the .desktop file points to.

Filezilla installed from the repos will put a desktop file in  /usr/share/applications.  That could be edited to use your executable, I  believe. Worth a try, at least.

If you're using a menu added via a Gnome extension, I suspect you'll need to find out how that extension works. Perhaps  the extension doesn't check for desktop files in user directories.

---

### Post by mJayk on 2014-11-29
Have a look at installing alacarte its in the repos and provides a gui to add programs to the list.

---

### Post by Dennis N on 2014-11-29
I decided to install it just to see if and how it worked. It does.

My steps:

Get program:

Downloaded **FileZilla_3.9.0.6_x86_64-linux-gnu.tar.bz2** from SourceForge.net
Extracted the folder **FileZilla3** to Desktop, then moved it to **/opt**
Tested it first to see if it runs:
```
dmn@Erica:/opt/FileZilla3/bin$ ./filezilla
```
It does.

Make Menu Entry:

I used a menu editor (alacarte) as suggested by mjayk. Good one. I am not acquainted with the Gnome Desktop but if possible, I suggest you try that - its easy to use if its available. To be accurate, I did this in Ubuntu MATE. Its menu editor is called MoZo, but probably is the same basically as alacarte - it's interface looks the same to me.

I put my entry under System Tools: In the editor, select the Category in the left pane, then on the right, "+New Item".
In the dialog, I entered the name, then the command **/opt/FileZilla3/bin/filezilla**. You can browse to the executable too to insure the right path.
Close the dialog. I see the correct icon was automatically used, and the entry is now in the menu.

I tested the menu entry. That works also, and Filezilla starts up, seems ok, but I did not test it yet to transfer files.

MoZo automatically made this .desktop entry in **~/.local/share/applications**:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=filezilla
Name[en_US]=Filezilla
Exec=/opt/FileZilla3/bin/filezilla
Comment[en_US]=Filezilla FTP Client
Name=Filezilla
Comment=Filezilla FTP Client
Icon=filezilla

```

So you should be able to do it manually too by just putting this in that location as a text file, filezilla.desktop.

---

### Post by meanmrmustard on 2014-11-29
Thanks!

---

### Post by meanmrmustard on 2014-11-29
Alacarte simplifies things, but..


I chose to save it in Applications, but after closing the dialog box, I found it in the menu under "Other" with a generic icon.

I found the .desktop file in .local/usr/share/applications labeled as alacartemade.desktop - until I made it executable then it changed to filezilla3.desktop.
I wan't able to open it in gedit, "open" was the only choice, "not open with" although clicking the icon or choosing "open" did launch the correct version as does clicking the icon from main menu/other.

---

### Post by deadflowr on 2014-11-29
> **meanmrmustard said:**
> Alacarte simplifies things, but..


I chose to save it in Applications, but after closing the dialog box, I found it in the menu under "Other" with a generic icon.

I found the .desktop file in .local/usr/share/applications labeled as alacartemade.desktop - until I made it executable then it changed to filezilla3.desktop.
I wan't able to open it in gedit, "open" was the only choice, "not open with" although clicking the icon or choosing "open" did launch the correct version as does clicking the icon from main menu/other.

You can open gedit first to then open the file with gedits open option.
Or open gedit and drag and drop the file.

And is there a category called Applications in gnome? I thought all programs fall in the Applications menu.
Did you mean accessories?
For the record, though, all my accessory apps are listed in the category called Utility.
For instance my gnome-terminal
Categories=GNOME;GTK;Utility;TerminalEmulator;

And as far as icons go, it's hard to say what's going on, but sometimes a logout, login makes them show.
Also might depend on the permissions of said icons...

---

### Post by meanmrmustard on 2014-11-29
> **deadflowr said:**
> You can open gedit first to then open the file with gedits open option.
Or open gedit and drag and drop the file.


:facepalm:
I knew that!

> 
And is there a category called Applications in gnome? I thought all programs fall in the Applications menu.
Did you mean accessories?

No actually I meant Internet lol 
I'm blaming the turkey hangover.

The menu does in fact now show the program under Internet since I corrected my error.
> 
For the record, though, all my accessory apps are listed in the category called Utility.
For instance my gnome-terminal
Categories=GNOME;GTK;Utility;TerminalEmulator;

And as far as icons go, it's hard to say what's going on, but sometimes a logout, login makes them show.
Also might depend on the permissions of said icons...

I'm going to let it go for today. I have a very large backup going on and would rather not interrupt it but I'll see
if logging in again resolves it at some later date.

Thanks for the input.

---

### Post by meanmrmustard on 2014-11-29
That sounds like the simplest solution.
I'll also look into the Gnome extention bit.
Thanks

---

### Post by Dennis N on 2014-11-29
It's interesting that in the .desktop file MoZo created (post #11), there is no **Categories=** key. I wonder how the menu is generated if it is not there?

---

### Post by monkeybrain20122 on 2014-11-29
If you cd to .local/share/applications and run ls (in the terminal) you will see all .desktop files created by alarte have the same names: alacartecreated1.desktop, alarcartecreated2.desktop etc. :) I would rather do it manually (just need to look at a template from /usr/share/applications)  Anyhow in your case Filezilla already creates a .desktop file all you need is to edit it to suit your need and remember to make it executable.

---

