---
title: "Python Script Click to run"
date: 2014-05-03
forum: General Help
---

### Post by 3dmatrix on 2014-05-03
Well, I know there are many querries on this topic and I tried the suggestions posted but still it does not works for me so I am starting a thread here. I also tried on the Python forums but some of them suggest asking Ubuntu community and vise-a-versa !

I am learning Python programming and make some simple games but I wish if I can run those .py files just by clicking (or double clicking) on its icon on the desktop.
I have added _#!/usr/bin/python_ in my script and made it _executable_ from the properties dialogue box but still when I click on it I get the "**Run in Terminal, Display, Cancel, Run**" dialogue box.

When I use the "Run in terminal" or "Run" button, nothing happens. When I type in terminal _filename.py_, it says _command not found_, even if I can see the file there and the terminal path is correct. If i use _python filename.py_ instead of that then it works fine.

But always working through the terminal makes it less enjoyable, esp if it is a game. Just for info, I use PyGame graphics libraries for the games in Python.

Can any one advise.

---

### Post by TheFu on 2014-05-03
What end-of-line character is used in the file?  Using MS-DOS editors with CRLF is bad.

Optionally, have you created a filename.desktop file to explain to whatever desktop running how to run the file?  This really shouldn't be needed.

---

### Post by 3dmatrix on 2014-05-03
> **TheFu said:**
> What end-of-line character is used in the file?  Using MS-DOS editors with CRLF is bad.

Optionally, have you created a filename.desktop file to explain to whatever desktop running how to run the file?  This really shouldn't be needed.

**I do not use any MS product on my computer !**

When I create a desktop shortcut file with the following content :
[B]
[Desktop Entry]
Version=1.0
Name=TileGame
Comment=Memory Game using Python and PyGame
Exec=/home/user/tilegame.py -ui
Path=/home/user/Desktop/
Icon=/home/user/.icons/download_folder-512.png
Terminal=false
Type=Application
Categories=Utility;Application;[/B]

On executing that file I get the following error :

[B]There was an error launching the application.
Details: Failed to execute child process "/home/user/tilegame.py" (No such file or directory)[/B]

Both the code file and the desktop file have execute permission.

---

### Post by TheFu on 2014-05-03
This may be a stupid question, but is "user" in /home/user/tilegame.py replaced by the real userid?

What is the output from 
```
ls -al /home/user/tilegame.py 
```

Please check also that there are no CRLF inside the file.

---

### Post by dragonfly41 on 2014-05-03
Another approach to locate your file ...

**sudo updatedb**

<wait a few minutes until index created .. then>

**sudo locate tilegame.py**

What do you see as return?

---

### Post by TheFu on 2014-05-03
I just noticed the issue.  Running "filename.py" won't work unless ./ is in the PATH.  To run an executable program in the current directory, that is NOT in the path (under bash), use ./filename.py - does that make sense?
Or you can use the full path to the program
Or you can set the directory where the script is located into your PATH (provided the shell does an auto-rehash). Some shells do not auto-find programs with execute permissions and need to be manually rehashed ... tcsh/csh fall into that group.

Anyway, hopefully 1 of those ideas will solve this.

---

### Post by 3dmatrix on 2014-05-03
> **TheFu said:**
> This may be a stupid question, but is "user" in /home/user/tilegame.py replaced by the real userid?

What is the output from 
```
ls -al /home/user/tilegame.py 
```

Please check also that there are no CRLF inside the file.

**-rwxrwxr-x 1 user user 5351 May  3 2:39 /home/user/tilegame.py**

What is **CRLF** ? and how do I check it ?

---

### Post by 3dmatrix on 2014-05-03
> **TheFu said:**
> I just noticed the issue.  Running "filename.py" won't work unless ./ is in the PATH.  To run an executable program in the current directory, that is NOT in the path (under bash), use ./filename.py - does that make sense?
Or you can use the full path to the program
Or you can set the directory where the script is located into your PATH (provided the shell does an auto-rehash). Some shells do not auto-find programs with execute permissions and need to be manually rehashed ... tcsh/csh fall into that group.

Anyway, hopefully 1 of those ideas will solve this.

You mean the **Path=/home/user/Desktop/** in the .desktop file ?
So what should it be ? **Path=./home/user/Desktop/ **  ?
What is this manual rehash ?

---

### Post by 3dmatrix on 2014-05-03
> **dragonfly41 said:**
> Another approach to locate your file ...

**sudo updatedb**

<wait a few minutes until index created .. then>

**sudo locate tilegame.py**

What do you see as return?

when I entered :
**sudo locate tilegame.py**  it displayed the corect path
/home/user/tilegame.py

but when I double clicked the file it sayed :
**Failed to execute child process "/home/user/tilegame.py" (No such file or directory)**

---

### Post by 3dmatrix on 2014-05-04
I solved the problem :

in the TileGame.desktop file I changed the following line by adding the python prefix :

Exec=**python** /home/matrix/tilegame.py  -ui

And it did the job. Now I can just double click on the icon and run that game.
Thanks every one.

---

### Post by TheFu on 2014-05-04
It was an issue with the program you are using to start the program. It wasn't honoring the agreed standards for scripts which involve reading the 1st line of a file to determine which interpreter should be used. Shame on them.  There really shouldn't be ANY NEED for a .desktop file at all.

---

### Post by 3dmatrix on 2014-05-04
> **TheFu said:**
> It was an issue with the program you are using to start the program. It wasn't honoring the agreed standards for scripts which involve reading the 1st line of a file to determine which interpreter should be used. Shame on them.  There really shouldn't be ANY NEED for a .desktop file at all.

You mean the python interpreter ? Or some problem at the OS level ?

---

### Post by TheFu on 2014-05-04
There is very little about launching a program that is "OS level" - everything that you and I use to do that is just another program - the entire GUI you are running is NOTHING SPECIAL - just another program. Bash is nothing special either - just another program. So - what program were you using to click on the desktop icon? THAT is the one that failed to follow nominal standards for launching a script. Some DE, I suppose?  Try launching the program using some other GUI - perhaps nautilus, pcmanfm or thunar ... does it work or not?

The .desktop file is something created by ... er ... I don't know ... feels like a .PIF file from Win3.0 days. I'm not a fan, as you can guess. I can imagine Linux viruses installed as .desktop files that could to unbelievable damage to a system, user-account, entire corporation.  It would be impossible for an AV tool to scan them for "badness."

---

