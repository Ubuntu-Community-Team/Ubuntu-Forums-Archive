---
title: "General plea for help"
date: 2007-06-03
forum: General Help
---

### Post by lordmaude on 2007-06-03
I have been a Windows user and I have just loaded Ubuntu 7.04 onto my laptop.
I'm completely lost and slightly annoyed.
I have a number of issues which I want to get sorted out....

1. every time i boot up i have to type in my wifi password. I discovered keyring manager but it's confusing, somebody mentioned your network password has to be the same as your Ubuntu login. Well my Ubuntu login is too simple for my security protocol for the network.


2. Installing programs. For instance, I want to use something other than the embedded bit torrent software as the GUI and management tools are too simplistic. So I downloaded utorrent (it said it was linux compatible) but the exe won't run.
How do you install programs in Ubuntu?

3. Networking.     I have previously had a workgroup set up between my 2 pc's.    Now that one is Ubuntu how do I share files?

So far these are the burning questions I have. Someone's help would be greatly appreciated.

---

### Post by dpar on 2007-06-03
I don't know about the wireless stuff, but use ktorrent. It's very similar to utorrent and it's in the repositories.

---

### Post by bishop9226 on 2007-06-03
do a couple of things -

to turn off having to enter the keyring over and over again, follow this guide - 

[http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html](http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html)

doesnt feisty come with azureus?  that is an excellent bit torrent prog, you can use that.  

download automatix @  [http://www.getautomatix.com/](http://www.getautomatix.com/)

it will give you a bunch of other progs you can download and remove easily.  you can also go to applications -> add/remove 

i recommend amarok for mp3s.

i dont know if there is a utorrent for linux or not, but if you just have the exe you can use that.  download WINE (you can download it from automatix under "Virtualization").  Then once WINE is installed, you should be able to right click on any EXE file and click "open with WINE").  If right clicking doesnt work, open up a terminal and type in: winefile 

it will open a file manager, you can then find your utorrent.exe file and double click it, it will run perfectly. THEN you should be able to right click it from here on and open with winefile.  you can also create a launcher for it so you can have a shortcut on your desktop.  i did this for quicktime pictureviewer and it works great.

ok as for networking two pc's you should be able to search the forums and find something or search google.  usually 500 people have already had the same question and you will be able to find an answer.

---

### Post by H.E. Pennypacker on 2007-06-03
> **lordmaude said:**
> 
2. Installing programs. For instance, I want to use something other than the embedded bit torrent software as the GUI and management tools are too simplistic. So I downloaded utorrent (it said it was linux compatible) but the exe won't run.
How do you install programs in Ubuntu?

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by bishop9226 on 2007-06-03
also keep in mind if you use wine w/ utorrent it will take up more memory than utorrent did on windows, so my advice is to use azureus.  its just as good.

---

### Post by YokoZar on 2007-06-03
> **bishop9226 said:**
> also keep in mind if you use wine w/ utorrent it will take up more memory than utorrent did on windows, so my advice is to use azureus.  its just as good.uTorrent runs great in Wine.  Top shows it using less memory (1.1%) on my computer than nautilus, gedit, and Gaim.

---

### Post by hank hill on 2007-06-03
automatix is AWESOME!

---

### Post by bishop9226 on 2007-06-03
> **YokoZar said:**
> uTorrent runs great in Wine.  Top shows it using less memory (1.1%) on my computer than nautilus, gedit, and Gaim.

yeah but it still uses mroe memory than azureus.

---

### Post by Beernut on 2007-06-03
[QUOTE=lordmaude]

2. Installing programs. For instance, I want to use something other than the embedded bit torrent software as the GUI and management tools are too simplistic. So I downloaded utorrent (it said it was linux compatible) but the exe won't run.
How do you install programs in Ubuntu?[/QUOTE]

uTorrent is really a windows program to get it to run you would need to setup Wine which probably isn't worth the trouble just for a torrent client.

From the uTorrent site.

"For Wine, Windows 95 (Winsock2), 98/ME, NT/2000, XP and above."

If you install Automatix like suggested you can install Azureus with just a couple of clicks.  To install other software try going to System  > Administration > Synaptic Package Manager.

[QUOTE=lordmaude] Networking.     I have previously had a workgroup set up between my 2 pc's.    Now that one is Ubuntu how do I share files?[/QUOTE]

To connect to your Windows share try going to Places > Connect to Server after filling in the information you should see a mount folder for your share on your desktop.

Hope this helps.

---

### Post by Beamerboy on 2007-06-03
> **bishop9226 said:**
> also keep in mind if you use wine w/ utorrent it will take up more memory than utorrent did on windows, so my advice is to use azureus.  its just as good.

I would recommend not using Azeurus for a number of reasons that I can't really go into on a public forum.  Deluge is a great torrent client for linux though and is written by an UbuntuForums member.  Not sure if it is in the Feisty repo's though.

Paladine

---

### Post by rbmorse on 2007-06-04
> **Beamerboy said:**
> I would recommend not using Azeurus for a number of reasons that I can't really go into on a public forum.  

Paladine

You realize that without amplification what you wrote is meaningless. 

RBM

---

### Post by pak33m on 2007-06-04
lordmaude,

> 1. every time i boot up i have to type in my wifi password. I discovered keyring manager but it's confusing, somebody mentioned your network password has to be the same as your Ubuntu login. Well my Ubuntu login is too simple for my security protocol for the network.

You should only have to type in your wifi network password once.  At the same time you will be prompted, upon first connecting, to enter credentials for the keyring. It maybe the keyring password that you are having to type in every time instead of a network password.

> 2. Installing programs. For instance, I want to use something other than the embedded bit torrent software as the GUI and management tools are too simplistic. So I downloaded utorrent (it said it was linux compatible) but the exe won't run.
How do you install programs in Ubuntu?

You do not have t use BitTorrent.  I have been using Deluge for quite some time without any problems.  Also, you might want to check into using Opera as a browser which has a torrent down loader built-in! What others have been trying to explain here is that you could run utorrent through the Wine program.

> 3. Networking. I have previously had a workgroup set up between my 2 pc's. Now that one is Ubuntu how do I share files?

There are just so may ways of going about this.  I think this was the easiest for me with regards to setting it up between Windows and Ubuntu: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way)

For most the aforementioned questions though I would read through the Feisty Guide to see how you would like to do it all.  It really is a great starting point and is that the point  - to do it all yourself (with the help of other too) [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Or you could you the built-in Ubuntu Help Center.

---

