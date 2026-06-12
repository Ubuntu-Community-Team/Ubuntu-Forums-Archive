---
title: "Can't Get Wine To Work... Please Help"
date: 2007-06-13
forum: General Help
---

### Post by Saxomophone on 2007-06-13
Hi, I'm trying to install wine. I followed their directions to install using the synaptic package manager, but i don't get the items in applications menu, and a search revealed no files labelled wine anywhere on my hdd. PLEASE HELP. I'm completely new to linux, so I don't know much of what I'm doing.

---

### Post by Citizin on 2007-06-13
When i used WINE, most of my windows apps ran slow and laggy.

If you want something a step up, try Crossover Linux, just google it, its just like WINE, only in my opinion its 10x better.

---

### Post by arvevans on 2007-06-13
Pull up a terminal screen:

"cd $HOME"  # this insures that you are in your home directory.

"ls -la"            # this is equivalent to windows "dir" command but the "a" lets you see hidden files & directories.

If you see a normally hidden directory called ".wine:" in your home directory, that is the start point for your windows emulation.

"cd ./.wine"

"ls -a"

You should see a pair of directories, one named "dos_devices" and the other named "drive_c".  Presence of these directories and files will tell you if wine is installed for your user ID.

"cd ./drive_c"

"ls -a" and you should see "Program Files" and "windows" directories.

"cd ./windows"

"ls" and you should see some .exe files, including notepad.exe

"./notepad.exe" and after a few seconds delay you should see the windows notepad appear on your screen.

At this point you can exit notepad and also exit your terminal session.  Now, when you download windows .exe files you can install or execute them with the terminal command "wine filename.extension" or simply right-click on them in the Linux file browser and select "wine" to execute them.  I prefer to initially run windows file installs using the command line "wine filename.extension" because it lets me see error conditions like missing .dll files and such.

One final check...pull up a terminal screen and enter "wine notepad.exe".  If the notepad screen comes up you know that you can run windows programs from a command prompt.  At this point you can build a command launcher to start "notepad.exe from an X-window.  Just remember to prefix the application name with "wine" (i.e. wine application_name.extension).

I will leave it up to you to build a Linux menu entry for "Windows" applications, and to add launchers to your windows applications in that menu.

Most problems with wine not properly executing windows programs can be traced to missing .dll files.  These can be found with Google searches and installed as needed.
_._

---

### Post by Saxomophone on 2007-06-13
./notepad.exe when in the windows directory won't open notepad "run-detectors: unable to find an interpreter for ./notepad.exe" if I "wine notepad.exe" it will open. I can't choose wine from the list of programs to 'open with" when i try to open a .exe

Can I make linux automatically use wine to do that? or do I need to go into console every time?

Thank you for your help.

---

### Post by misha680 on 2007-06-14
> **Saxomophone said:**
> ./notepad.exe when in the windows directory won't open notepad "run-detectors: unable to find an interpreter for ./notepad.exe" if I "wine notepad.exe" it will open. I can't choose wine from the list of programs to 'open with" when i try to open a .exe

Can I make linux automatically use wine to do that? or do I need to go into console every time?

Thank you for your help.

Open with should have a "> Custom" at the bottom. Just click on the
little thing (not sure what to call it) to the left of Custom and you can type
whatever command you want, like
```
wine
```
to run .exe files with wine.

Misha

---

