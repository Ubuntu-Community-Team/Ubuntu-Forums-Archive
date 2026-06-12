---
title: "How to make Steam.exe icon on desktop"
date: 2007-05-24
forum: General Help
---

### Post by Warsaw on 2007-05-24
I have fooled around with this alot and cant seem to get it right. Basically I want an quicklaunch icon on my desktop that I can click and steam will run. I tryed using the steam.exe in the foldler but that didnt work. When i click the icon I need it to be able to run steam with wine that way I dont have to use terminal to run it.

---

### Post by Famicommie on 2007-05-24
It sounds like you need to make a simple shell script, and then add that shell script to your panel/menu.

What command do you run from the terminal in order to get WINE run steam?

---

### Post by Warsaw on 2007-05-24
/home/david/.wine/drive_c/Program\ Files/Steam/ then I do wine Steam.exe

---

### Post by Famicommie on 2007-05-24
So let me make sure I have this right...

First you issue the command
```
cd /home/david/.wine/drive_c/Program\ Files/Steam/
```
And then you input the command
```
wine steam.exe
```

Does that sound about right?

If not, post the detailed process that you go through in order to open up steam. We are going to write something called a shell script, which is a single or sequence of command(s) that will automatically run by clicking on a link to the script. It will be much faster than typing out everything, but in order to write it properly I need you to lay out exactly how you run steam every time. Step by step, please.

---

### Post by Warsaw on 2007-05-24
yep that is correct

---

### Post by Brynster on 2007-05-24
you could just simply drag the menu entry from the gnome menu's onto your desktop and that will create a desktop launcher for you.

---

### Post by Famicommie on 2007-05-24
Oh, okay then. We will have to jump to the terminal again (but only for a minute).

First, use the text editor and insert the following text:
```

#!/bin/bash

wine /home/david/.wine/drive_c/Program\ Files/Steam/Steam.exe
```
Save it in your home directory (/home/david) with the name Steam

Now, open up that terminal and issue the command
```
chmod u+x Steam
```

Let's do a quick recap. A shell script is essentially a text file which tells Linux "do the things I have put in this file". The chmod command is telling Linux to make the file 'executable'. Now, from the terminal issue the command
```
sudo mv Steam /usr/bin
```
Which will put the script we have just made into the PATH, or the area that Linux looks when it is given a command. Unless you have told it to, Linux does not look in your home folder for executables. It only looks in a select few places. /usr/bin is a great place to keep most things. But anyways...

Right click on the center of the top panel and select the command "Add to Panel". From there, click on the button that says "Custom Application Launcher". It will bring up a dialogue with several fields. For the name, put "Steam" and for the command put "Steam". Feel free to select an icon to use for it. Once you have finished, click on the "OK" button. From now on, there will be an icon on the panel that will run Steam every time that you click on it. If, for some reason, it doesn't work, open up a terminal and type "Steam" and report any errors that you recieve.

If it does work, let us know so that we can all rest peacefully ;)

---

### Post by Warsaw on 2007-05-24
Yes it will but it will not run. I cannot drap and drop the steam.exe onto desktop and have it run since this is a windows app it needs wine.

---

### Post by Warsaw on 2007-05-24
~

---

### Post by Warsaw on 2007-05-24
~

---

### Post by Warsaw on 2007-05-24
Sorry for the ~ post I found all the problems and couldnt delete post. Well I try running it and I see steam start and then I get this error   "Could not load module 'bin/vgui2.dll'

---

