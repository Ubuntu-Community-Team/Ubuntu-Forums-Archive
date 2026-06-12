---
title: "Bunch of Questions"
date: 2008-05-15
forum: General Help
---

### Post by smmalis on 2008-05-15
1. Is there a way to control whether or not my flash drive gets mounted when I plug it in? (it has two partitions, I only want 1 of them most of the time)
2. Where is the GNOME menu located? (so I can gedit it)
3. Why are some applications out of date? (Transmission, ClamAV)
4. Is there a way to remove the NVidia splash screen on startup?
5. Is it safe to enable the proposed update repositories?
6. Anyone know of a good casual game to pass the time? (native or in Wine) Solitaire and Minesweeper only last so long.

---

### Post by ivze on 2008-05-15
1.
 1)ls /dev/sd*
 2)plug in flash drive
 3)ls /dev/sd*
 compare results. If mounted, new entries like sda1, sdc1 ... will appear.
2.
 Isn't that what appears at pressing left upper symbol of Ubuntu??
3. 
 -------------(don't use them)
4. 
 ATI user =P
5.
 Not sure, didn't change anything since install.
6.
 See wormux (0.8beta4 is in Hardy repository, however, the community is going to release 0.8 final soon. Building current SVN from sources is also a nice time-pass =P). See #wormux channel at freenode.

---

### Post by argraff on 2008-05-15
6. Check out SoulFu at [www.aaronbishopgames.com]("http://www.aaronbishopgames.com"). There's a linux .deb there, I believe. Very cool, fun game!

---

### Post by bingoUV on 2008-05-15
Games : 
1. Tuxpuck : Very easy to play, very hard to win.
2. PowerPenguinRacer : aka tuxracer, ppracer etc. Many tracks and variations. A bit demanding on graphics side but you have nvidia graphics so should not be a problem. Can spend a long time.
3. Powermanga : Can spend a week or two.
4. xgalaga/xgalaxy : Some more weeks here.
5. Frozen bubble : Between the other games.
6. SuperTuxCart : I am new to it, but almost as good as PowerPenguinRacer.

**All** available in repositories. Very simple, no concepts to learn, no strategies to formulate. Just kill time.

---

### Post by darco on 2008-05-15
> **smmalis said:**
> 1. Is there a way to control whether or not my flash drive gets mounted when I plug it in? (it has two partitions, I only want 1 of them most of the time)
2. Where is the GNOME menu located? (so I can gedit it)
3. Why are some applications out of date? (Transmission, ClamAV)
4. Is there a way to remove the NVidia splash screen on startup?
**5. Is it safe to enable the proposed update repositories?**
6. Anyone know of a good casual game to pass the time? (native or in Wine) Solitaire and Minesweeper only last so long.

I too want to know about "proposed updates". This AM I donwloaded "proposed updates" so what does that really mean and what actually downloads.
Also I noticed in my x64 system the download alert changed to a a RED arrow. In my 32 bit system its still an orange icon?
oh well
darco

---

### Post by manicman on 2008-05-15
Try the command
```
sudo nvidia-xconfig --no-logo
```
to remove the nvidia splash screen

---

### Post by smmalis on 2008-05-16
> **smmalis said:**
> 
1. Is there a way to control whether or not my flash drive gets mounted when I plug it in? (it has two partitions, I only want 1 of them most of the time)
2. Where is the GNOME menu located? (so I can open it in gedit)
3. Why are some applications out of date? (Transmission, ClamAV)
5. Is it safe to enable the proposed update repositories?


Thanks for all the answers so far!

---

### Post by atomkarinca on 2008-05-16
> **smmalis said:**
> 2. Where is the GNOME menu located? (so I can gedit it)

Right-click on the menu and select edit menu.

> 3. Why are some applications out of date? (Transmission, ClamAV)

AFAIK they are updated if there's a security update.

> 6. Anyone know of a good casual game to pass the time? (native or in Wine) Solitaire and Minesweeper only last so long.

Definitely [Kobo]("http://olofson.net/kobodl/"), go nuts :)

---

### Post by strabes on 2008-05-16
1) Beyond me.

2) Please clarify what you mean by GNOME menu? Are you thinking of an XML file which you can edit to change the menu? You can edit the Applications, Accessories, System menu by going to System > Preferences > Main Menu.

3) New versions of applications must be put into the ubuntu repositories before you are able to automatically update. This understandably takes time, and sometimes versions of applications are purposely left out of date in the repositories for the sake of stability. There are specific requirements which updates must fulfill in order to be put in the repositories of an existing ubuntu release. Oftentimes simple updates of applications do not meet these requirements and are therefore not put into the repositories. If you can find an updated .deb package of the application you are looking for, go for it.

5) Do not know, but would not recommend it. If it ain't broke, don't fix it.

6) I love freecell solitaire; it's included by default in ubuntu.

---

### Post by smmalis on 2008-05-16
I know you can edit it with a right click, but is there an xml file or something similar so I can open it in gedit?

---

### Post by Therion on 2008-05-16
> **smmalis said:**
> 
5. Is it safe to enable the proposed update repositories?
Define "safe"...

I would say it all depends on your risk tolerance. For instance, do you consider running an Alpha version of your preferred OS "safe"?  How do you feel about reinstalling?  

If you answered "No" and "Sick to my stomach," I can't suggest you enable the "Proposed" repos.

---

### Post by atomkarinca on 2008-05-16
> **smmalis said:**
> I know you can edit it with a right click, but is there an xml file or something similar so I can open it in gedit?

AFAIK there isn't one. Although if you want to add an application manually you should create a .desktop file in /usr/share/applications.

---

### Post by smmalis on 2008-05-16
Then the following questions remain:
> **smmalis said:**
> 1. Is there a way to control whether or not my flash drive gets mounted when I plug it in? (it has two partitions, I only want 1 of them most of the time)
6. Anyone know of a good casual game to pass the time? (native or in Wine) Solitaire and Minesweeper only last so long.

---

### Post by strabes on 2008-05-16
In the repositories: chromium, nexuiz (fps), planet penguin racer (really fun), zsnes (snes emulator)

---

