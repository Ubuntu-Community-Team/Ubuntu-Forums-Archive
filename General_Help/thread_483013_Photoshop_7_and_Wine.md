---
title: "Photoshop 7 and Wine"
date: 2007-06-24
forum: General Help
---

### Post by DrTsus on 2007-06-24
The Ubuntu Guide Wiki didn't help, so I need to ask it here. Well, I installed Wine, and I have unzipped my Photoshop 7. Now, do I need to open setup.exe with Wine? Or do I have to go about it some other way? And can someone explain how I run something with wine. I might have an idea,but what command do I use? 

Thanks in advanced! Sorry, I'm new to this.

---

### Post by JimNSB on 2007-06-24
> **DrTsus said:**
> The Ubuntu Guide Wiki didn't help, so I need to ask it here. Well, I installed Wine, and I have unzipped my Photoshop 7. Now, do I need to open setup.exe with Wine? Or do I have to go about it some other way? And can someone explain how I run something with wine. I might have an idea,but what command do I use? 

Thanks in advanced! Sorry, I'm new to this.

Just a noob, but from what I read clicking on the unzipped .exe _should_ launch Wine, which then launches the program's installer.

---

### Post by pavpan on 2007-06-24
> **DrTsus said:**
> The Ubuntu Guide Wiki didn't help, so I need to ask it here. Well, I installed Wine, and I have unzipped my Photoshop 7. Now, do I need to open setup.exe with Wine? Or do I have to go about it some other way? And can someone explain how I run something with wine. I might have an idea,but what command do I use? 

Thanks in advanced! Sorry, I'm new to this.

You can run something in wine in two ways, but the easiest is:

Right click on setup.exe or whatever exe you should run (to install a program, run its installer through wine)

Open With 
If you see "WINE Windows Emulator" or something like that click it

Otherwise:
Open With Other Application
Open With Custom Command
In the box type "wine"
OK.

That'll soon enough start showing up in the menu.

Have fun with Ubuntu!

---

### Post by Silenus on 2007-06-24
To test wine with photoshop I just poped in photoshop 5, and it installed no problem. Then I tried civ3, and motorola messenger, they did not work, even under crossover office emulation. But photoshop 7 should run fine under wine.

---

### Post by DrTsus on 2007-06-24
Wine isn't showing up anywhere and I followed the instructions on the Wine HQ website. [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Silenus on 2007-06-24
Wine doesn't show as an app in menu. And it's easier to install from the repositories, sudo apt-get install wine

Then you put the cd in, and look for the installer exe, right click and run with wine, if it doesn't work you can always try crossover office

---

### Post by DrTsus on 2007-06-24
I got it to start, but half way through the installer it stopped and disapeered.

---

### Post by Silenus on 2007-06-24
Sounds like crash from missing files. hm, have a look at cross over office, it might support it.

---

### Post by DrTsus on 2007-06-24
I think I finally got it to work. It's pretty buggy but I'm sure I'll figure something out eventually. My mouse just kept jumping around, but that could be Compiz. I don't know.

---

### Post by orko3001 on 2007-08-30
I thought I would try Filezilla as a test. It installed and said it would put an icon on the desktop. But it hasn't. It hasn't appeared in the applications menu either. I installed it following instructions above. I also installed Windows Media Player but again no luck. Firefox installed ok and is in the applications menu. 

Cheers for your advice :)

---

### Post by orko3001 on 2007-08-30
Ok

/home/myfolder/.wine/drive_c/Program Files/

---

