---
title: "Win dominated software on Linux (Wine?)"
date: 2007-04-18
forum: General Help
---

### Post by MiwaKi on 2007-04-18
Hi,

I'm new here, and new to all of this, frankly. I recently got fed up with windows to the point of switching to linux. I thought installation would be a nightmare... fortunately that was not the case. ^_^; But now I have a whole new set of problems. I've got windows-only software I absolutely need for my work, and other programs I just can't live without (photoshop, for instance).

Here come the questions/problems.

I've heard of wine, but I'm not sure if this is exactly what I need. All I know about it, actually, is it's supposed to let win-dominated software run on linux. Ok, great. Only, I have no bloody idea how to install this thing. I got it downloaded, and it's sitting on my desktop, but there's no (working) installation file that I can find. (Keeping in mind, as far as I know, if it says 'install' anywhere in the name, I'd take it for the file I need. I'm that much of a newbie.)

Of course it occurs to me now, I'm still thinking very much like a windows junkie. In windows, you point and click, and windows does everything for you. I realize that this is not really always the case with linux. In fact, the horror of having to deal with command prompts (which I haven't done since the DOS days), was enough to make me almost not even try to switch to linux. But if I can make it work, I'd like to switch.

[B]Ok, so what I need help with here is this... 

Problem: need to be able to run windows only software on my (ubuntu) linux, and am a total and complete linux "newb."

Possibly mistaken notion of the answer: get wine, which as far as I understand, will solve this problem.

More problems: I have no idea how to install it, even with the 'readme' open.

SO... is this really what I need? (Considering I need to run obscure win software like NJStar Japanese word processor?) And, if it IS what I need, how the heck do I install it so that I can even install my "win-ware"? OR... is there something easier out there that will allow me to run (even obscure) win software, without having to shell out big money to do it?[/B]

Please help if you can...

Thanks.
-Ki

---

### Post by raja on 2007-04-18
wine is available in Ubuntu's repos. So all you have to do is type ```
sudo aptitude install wine
```in the terminal. Or open synaptic, search for wine, select it and click install. Once you have it you can right click on the .exe which is the installer for you windows app and select 'open with wine'. Wine will create a c: drive and all and instal the app just as in windows. However, not all windows apps work with wine. Check the wine site - they maintain a database of the apps that work well. 
An alternative is to use a virtual machine running windows. If you have more than about 700 MB of RAM, this is a better option, in my opinion. Both VMware and VirtualBox work very well for this.

---

### Post by spankymasterc on 2007-04-18
What software are u trying to install first of all?

Next wine isnt very easy to understand but there are several tutorials ....

Here i looked around and i found this how to for you:
[http://ubuntuforums.org/showthread.php?t=149585&highlight=wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine)

It shows you how to setup wine.....

You could try this 2 its easier but less explanation:
[http://ubuntuforums.org/showthread.php?t=56892&highlight=wine](http://ubuntuforums.org/showthread.php?t=56892&highlight=wine)


Well if u need more personal help or what not feel free to hit me up on msn,aim, or yahoo check profile for screenname 

::cheers::

---

### Post by MiwaKi on 2007-04-18
Hmm... it says it's installed now, but my software complains nothing recognizes the install file (eg, nothing can run the installer for my win software.) Do I need to download something special to get windows-program setup files to open?

Thanks for your help by the way!

---

### Post by raja on 2007-04-18
From a terminal, you can just type ```
wine setup.exe
``` (If setup.exe is in the current directory. To do it from the file browser, right click on the exe and choose 'open with other application' and in 'custom application', type wine. 
You might also want to look at [wine tools]("http://www.von-thadden.de/Joachim/WineTools/") which simplifies installation of many windows applications.

---

### Post by jimbean on 2007-04-18
try cedega and or codeweavers they talk the talk but i dont know if they walk the walk
maybe help, if you have the $$$$

---

### Post by spankymasterc on 2007-04-18
try doig this right click on the setup.exe file and click open wiht other application the click use custom command and type gnome-wine and enter :D cheers:D

---

### Post by Espreon on 2007-04-18
Becaureful of Winetools since it can screw up Wine (from what I have heard). Try Wine-Doors, it is like Wine-Tools but it has more features like GNOME menu integration with Wine drive, application respitories and more. And it should make it so you can double-click on an exe to run it. here ya go: [http://www.wine-doors.org](http://www.wine-doors.org)
 
To install Wine-Doors you will need a Subversion client, so 1st fire up the Add.Remove programs thingy, 
search for kdesvn.
Install it, then chechout a respitory, for the respotroy type in [http://www.wine-doors.org/svn](http://www.wine-doors.org/svn)
then check out the wine-doors directory to whereever. Now open the terminal andf goto the wine-doors repitory ya checkout, then in the terminal type python, drag the setup.py to the terminal window and the type install. and then goto system tools wine-doors and enjoy.

---

### Post by Dyegov on 2007-04-18
I had exactly the same problem before. I am going to install 7.04 tomorrow (Once it is released) and I want to know:

Does wine work with WLM (Windows Live Messenger), FileZilla (FTP program) and no$GBA (A GBA NDS emulator) ?

---

### Post by raja on 2007-04-18
You can check out how well something runs in wine in the database maintained by the wine developers [here.]("http://appdb.winehq.org/")  All the same, try to check out the natively available alternatives. There should be many good programs for FTP. And I think amsn should work like windows live messenger (though I may be wrong).

---

### Post by rogblake on 2007-04-18
> **MiwaKi said:**
> Hi,
Possibly mistaken notion of the answer: get wine, which as far as I understand, will solve this problem.
i

It really depends on the application. Some work with wine, many do not. There is a commercial wine variant called "Crossover Office" available which has been specifically tweaked to run Microsoft Office and some other Windows apps. (See [http://www.codeweavers.com/](http://www.codeweavers.com/) for details.)

Another possibility is to run Windows in a virtual machine using VMware. (I run Win98 under linux this way for Windows apps that are not compatible with wine.)

---

