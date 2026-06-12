---
title: "How To Get YahElite Working In Ubuntu"
date: 2008-06-18
forum: General Help
---

### Post by rage-against-windows on 2008-06-18
I searched the forums and didnt see anything about this yet so I thought for those of you who liked using YahElite in windows Id tell you how to get it working perfectly in Ubuntu.

First off, Im using Hardy Heron i686
Wine version 1.0 (The Newest Version)
Wine-Doors 0.1.2 (to install a couple needed files)
And last but not least YahElite minimal, although Im sure the full version would work just as good.

I installed wine 1.0 and set it up to use windows xp as the program default, then I downloaded Yahelite minimal. It works fine right out of the box, but you will notice the scroll is off by about a quarter inch. This is where wine-doors comes in handy. Use wine-doors to install native rich text editor support 3.0. This fixes the scroll problem and also fixes a small bug with the text showing up right in the chat area. Also for those who like using Yahoo "progs" using wine-doors to install visual basic runtime lib.6 will let you use all the "progs" you want. You can also install the c++ runtimes to use the newer stuff.

To add the newest wine to your repository I copied this from the winehq site...

Adding the WineHQ APT Repository:

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Hardy (8.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list

Then update APT's package information by running 'sudo apt-get update'.

After doing this the new version (1.0) will show in in your repo.

Here is the direct link to wine-doors...

[http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb](http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb)

And to get the latest version of YahElite, or Minimal YahElite visit [http://www.yahelite.org/deep/yahelite/](http://www.yahelite.org/deep/yahelite/)

Now I couldnt get Voice to work on YahElite because the site to download the cab files for it seems to be down, but I learned a trick using gyachi. You log in with gyachi first, and active voice, then log out gyachi but leave voice going, and then you can log into YahElite using the same ID. Pretty nice.
Here is a post about gyachi and how to get the latest version...

[http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi](http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi)

I hope this helps a few people who were big YahElite fans like I was, and it took me a while, and alot of trial and error to get it working as smooth as it does on windows, and I really wanted to share this with you guys, and girls....have fun!

---

### Post by rage-against-windows on 2009-02-22
I finally figured out how to get the Voice Chat feature to work in yahelite under Ubuntu. You will need to copy tssoft32.acm and tsd32.dll from a windows machine, if your like me, and dont have a windows machine handy just do a google search. I found a copy of both online and put them both in the wine/windows/system32 folder. Then open your windows/system.ini file and right under where it says drivers copy and paste this line. "MSACM.trspch=tssoft32.acm"

Make sure you run YCabby [http://www.yahelite.org/deep/yahelite/YCABBY.exe](http://www.yahelite.org/deep/yahelite/YCABBY.exe). When ou run YCabby make sure you change the H: to C: or what ever directory you have our .wine set up to. Now you should have a good strong VC working in Yahelite. Also by running the YCabby program it permits the Web Cam view feature to work, I did not test the Cam show feature, because I have no cam.

---

### Post by d3v1150m471c on 2010-02-22
Click on the link in my signature. It does all this crap for you and some.

---

