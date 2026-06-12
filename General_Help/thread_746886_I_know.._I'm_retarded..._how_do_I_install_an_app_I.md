---
title: "I know.. I'm retarded... how do I install an app I downloaded?"
date: 2008-04-06
forum: General Help
---

### Post by AquaStreak on 2008-04-06
Hello!

Today is the first day I've had Ubuntu. I have switched from Windows XP. I am having a problem with program installations.

The problem I am having is that.. I don't know what to do. I downloaded the Ubuntu version of Linux of Skulltag from [http://skulltag.com](http://skulltag.com).

After extracting the "Linux base" and the Ubuntu version, I put them in a folder. I get some files that have an icon in a diamond shape with some gears in them. These are executables. But they don't do anything if I click them.

What am I doing wrong?

Please help. Thanks!

---

### Post by Gen2ly on 2008-04-06
First of all, welcome to Linux!  Congrats you made the smartest choice of your life. ;)  Second those icons with gears are binarys and they are similiar to windows .exe's.  They can be run by clicking on them with a bit of setup, but it's usually easier just to run them from the command line.

Open gnome-terminal (in Accessories) and change to the directory where the downloaded files are.  If I'm being overly simple, I apologize.

```
cd ~/Desktop
```

cd means change directory, ~ is an abbreviation for the home folder.

Then change directories to the download folder.

Likely the binaries are not recognized as executable in Linux so make those gear-diamond icons executable by:

```
chmod +x program
```

Then to run them is simple just typing

```
./program
```

Hope this helps.

---

### Post by tubasoldier on 2008-04-06
Welcome to Linux. Hopefully Dirk.R.Gently's comments helped you. Feel free to ask if you have any more questions.

---

### Post by 67GTA on 2008-04-06
This helped me when I first started using Ubuntu: [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by depele on 2008-04-06
Hello, 
On how to forge you can find an excellent step by step setup for a perfect desktop.
[http://www.howtoforge.com/the_perfect_desktop_ubuntustudio_7.10]("http://www.howtoforge.com/the_perfect_desktop_ubuntustudio_7.10")
the how to of the link is for ubuntu studio. 
But this is similar for ubuntu.

grtz..

Arne

---

