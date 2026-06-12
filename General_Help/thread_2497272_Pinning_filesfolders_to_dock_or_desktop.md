---
title: "Pinning files/folders to dock or desktop?"
date: 2024-04-28
forum: General Help
---

### Post by cbiweb on 2024-04-28
There are spreadsheets, docs and a few other things I use often throughout each day.

In Windows I could keep them fairly close, either by pinning them to the taskbar (dock), or on the desktop, reachable by a Desktop menu in the taskbar.
Some of them were in a folder that was pinned to the taskbar or desktop.

Is there a way to do this or something similar in Ubuntu?

---

### Post by TheFu on 2024-04-29
Depends on the DE you are using. Some make it really easy.  Gnome doesn't think you should be allowed to have a cluttered desktop, so it isn't possible in the stock version.  There is at least 1 Gnome addon that will help make the "desktop" your own.  I don't use Gnome, so I don't know what that addon is, but   FOUND IT - "add to desktop" - #21 at this link [https://itsfoss.com/best-gnome-extensions/](https://itsfoss.com/best-gnome-extensions/)

Of course, if you aren't using Gnome as your DE, you'll need to check the manual for the DE you are using for how they recommend doing it.

I don't use any DEs.  I'm a pure WM-only user, so if I want something quickly available from a menu, I will manually add the menu item to my left-click menu that does what I want.  That can be to open a data file or run a program on a different computer that opens a data file or almost anything else.  For example, I like to have a Calculator handy and "galculator" is the name of the one I find acceptable.  The menu entry in my ~/fvwm/config file for it is this:
```
+                       "&f. Galculator" Exec exec /usr/bin/firejail /usr/bin/galculator
```
That probably isn't useful to you, since almost nobody here uses fvwm.

---

### Post by donald187 on 2024-04-29
I run Ubuntu 22.04.  I can move documents and folders from the Documents section of the Files app to the desktop by the usual drag and drop.  I believe this is possible because Ubuntu automatically installs the Desktop Icons NG Gnome extension.  Mind you it actually moves them.  It doesn't make a second copy.

Just for clarity you don't have to install the extension.  Ubuntu has already done it for you if you have the regular install.

```

$ apt list gnome-shell-extension-desktop-icons-ng
Listing... Done
gnome-shell-extension-desktop-icons-ng/jammy-updates,jammy-updates,now 43-2ubuntu1 all [installed,automatic]

```

[https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/)

Hmmm, doesn't seem to be quite what you were asking for.

---

### Post by vanadium on 2024-04-30
The Dock only contains applications from the application overview. You place them there yourself by pinning them to the Dock (Right-click an application in the application overview, and select "Pin to dock").

As indicated above, Ubuntu has a desktop on which you can place files. If you care about file management, be aware that a file placed on the desktop resides in a directory ~/Desktop. If you want the file to remain in the original location, create a link to the file and place the link on the desktop.

Next, there is the "Starred" items feature in the file manager. Drag those files to which you want quick access into the "Starred" folder in the left pane of the file manager. They remain in their original location, but will also appear in the "Starred" folder until you remove the star (right-click - unstar).

Note also that hitting "Super" and typing a few characters of the file name will reveal matching files. This is another way to rapidly gain access to specific files. Also within the file manager, search is prominent. Whenever you start to type, a search will be initiated.

---

### Post by vanadium on 2024-04-30
(double post)

---

### Post by dragonfly41 on 2024-04-30
My one stop shop for locating files is simply Recoll (discussed in earlier threads).
After indexing* all* files (and updating index daily/frequently) when I want to locate any asset I just use the query field. So Recoll launcher is seen in my docking bar, click on that, go to the button to right of Recoll query field (history of searches), pick the appropriate one, double-click on file name .. and I am there.

---

### Post by TheFu on 2024-04-30
In theory, **xdg-open** will look at the MIME type of any file, then open the correct application, passing in the data file to be used.  This is how file managers used to be able to open any data file before that was deemed a security risk by some.  If the file manager you use doesn't support opening a file via double-click, but does allow customized addons via a right-click menu, you could use **xdg-open $@** or something similar as the generic *open* command for nearly any data file.

That's the theory.

As for placing files on the desktop, if you just want a link on the desktop and not actually moving the file, there are symbolic links and hardlinks which can be used to make a file stored in a specific data directory also accessible on the desktop.  I don't know the GUI way to make a link, but the command line method is either **ln {source} {target}** for a hard link or **ln -s {source} {target}** for a symbolic/soft link.

Hard links only work within the same file system. Besides that, they behave like the actual file. Soft links can cross file system boundaries and are like a check you use to pay someone.  It says, I don't have any money, but if you ask these people by presenting this check, they will give you the money. If the bank is out of business, the check isn't any good.  Softlinks are like that.  They are a pointer to where the real file is located, but if the real file has been moved or deleted, then the softlink is useless.

---

### Post by dragonfly41 on 2024-04-30
One interesting use of xdg-open I have found is writing tutorials with embedded xdg-open hyperlinks to downloaded scripts which can run commands. So you can write the tutorial in HTML page, hit a point in workflow where commands need to be run, and they run on the desktop through a *.desktop link. Of course the reader must trust the sources of the tutorial but it beats having to copy and paste and run code sequences in tutorials. in short frequent documents or apps can be launched from an HTML index page.

---

### Post by donald187 on 2024-04-30
> **vanadium said:**
> 
Next, there is the "Starred" items feature in the file manager. Drag those files to which you want quick access into the "Starred" folder in the left pane of the file manager. They remain in their original location, but will also appear in the "Starred" folder until you remove the star (right-click - unstar).

The drag and drop doesn't work for me.  The Starred folder is greyed out and won't complete the drag and drop.  I have to right click on the document and select "Star".

---

### Post by tamarinblade on 2024-06-18
[FONT=Verdana]> **cbiweb said:**
> There are spreadsheets, docs and a few other things I use often throughout each day.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]In Windows I could keep them fairly close, either by pinning them to the taskbar (dock), or on the desktop, reachable by a Desktop menu in the taskbar.[/FONT]
[FONT=Verdana]Some of them were in a folder that was pinned to the taskbar or desktop. [[COLOR=#FFFFFF]basketball stars[/COLOR]]("https://basketballstars-game.io")[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Is there a way to do this or something similar in Ubuntu?[/FONT]
[FONT=Verdana]In Ubuntu, managing frequently used files and applications can be done through several methods similar to Windows. You can add applications to the dock on the left side of the screen for quick access by launching the application, right-clicking its icon in the dock, and selecting "Add to Favorites". This keeps the application readily accessible.[/FONT]

[FONT=Verdana]For documents and files, while Ubuntu does not display icons on the desktop by default, you can enable this feature through GNOME Tweaks. This allows you to place shortcuts or files directly on the desktop for easy access. Additionally, you can create desktop launchers for specific applications by right-clicking on the desktop, selecting "Create Launcher", and filling in details like the application name, command, and icon.[/FONT]

[FONT=Verdana]Ubuntu also supports pinning folders to the Files (Nautilus) application in the dock for quick file access. Utilizing keyboard shortcuts, GNOME Shell Extensions like "Dash to Dock", and customizing the Activities Overview further enhances accessibility and organization of frequently used items in Ubuntu, catering to your workflow preferences.[/FONT]

---

