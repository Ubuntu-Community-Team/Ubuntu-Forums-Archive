---
title: "cairo-dock always on top"
date: 2008-05-20
forum: General Help
---

### Post by RikoW on 2008-05-20
Dear all,

I installed cairo-dock in hardy following this guide:

[https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock")

It all seems to work fine and I kind of like it. Unfortunately, the dock stays always on-top off all windows, which I find kind of annoying and sometimes even disturbing the work.

So far, I haven't found out, to tell cairo-dock to allow other applications to cover it. I tried auto-hide, but that's not really a workable solution for me.

Thanks for any hint,

                 Riko

---

### Post by bobjenkins on 2008-05-20
try this

First installed ccsm:

```
sudo apt-get install compizconfig-settings-manager
```

Under the windows rules, click the PLUS on below , now click grab, then click on your dock, then it should work

---

### Post by RikoW on 2008-05-20
Shouldn't I put that in the 'below' field, if I want to allow other applications to cover the dock?

Anyway, I tried both, but doesn't seem to have any effect :(

- Riko

---

### Post by bobjenkins on 2008-05-20
I have edited the post to a better way, try it and post back, I have confirmed it works with firefox window, and vlc window, hopefully it will work with a dock also:) goodluck

---

### Post by RikoW on 2008-05-20
Unfortunately, still the same :(

Thanks for trying, though :)

---

### Post by bobjenkins on 2008-05-20
:( must not work with docks. 

Oddly when I am searching for a solution everyone wanting the opposite of you (they want it always on top, there dock is always below)

On the original link check out the section about auto hiding, might suffice until you find a solution :)You can set the opacity to 50% on autohide.  sorry couldn't help more goodluck

---

### Post by RikoW on 2008-05-20
> **bobjenkins said:**
> :( must not work with docks. 

Oddly when I am searching for a solution everyone wanting the opposite of you (they want it always on top, there dock is always below)


Yeah, I saw that, too! :) But, I often work with rdesktop connections to windows machines. And then the dock is covering the task bar and start menu of the remote host. Not very practical for working!

> 
On the original link check out the section about auto hiding, might suffice until you find a solution :) sorry couldn't help more

Tried that already, but was not satisfied - felt kind of 'clumsy'. Never really liked these auto-hide options. But maybe, I get by until I find a solution.

Thanks again for trying :)

---

### Post by RikoW on 2008-05-20
Just noticed something, though! The "below" setting in the window rules of compiz seems to work at least for all pop-up windows of the dock. All config windows pop up below the applications :)

Not really what I wanted, but it's a start :)

In the end, also the gnome panels are not covered by applications ...

---

### Post by bobjenkins on 2008-05-20
Someone else 4 weeks ago had this problem and no solution was found :( Probably not possible, the developers thought "autohide is enough" (personally I dont prefer autohide either) 


[http://ph.ubuntuforums.com/showthread.php?t=759618](http://ph.ubuntuforums.com/showthread.php?t=759618)

anyway goodluck finding a solution

---

### Post by fabounet on 2008-05-21
if you want always on top : cairo-dock --keep-above
if you want the opposite, check out the 1.5.6 version, the dock can automatically hide itself when a window becomes maximised or fullscreen :-)

---

### Post by RikoW on 2008-05-21
hmm, and where would I find the version 1.5.6?

---

### Post by neymac on 2008-05-21
> **RikoW said:**
> hmm, and where would I find the version 1.5.6?
Still Cairo-Dock (2007-2008)
 version 1.5.6-rc1 , using SVN at 
[http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en")

---

### Post by linuxsamurai on 2008-05-30
Hey guys i also had such problems for a while now and just literally figured out a way to get around this.

If you have Beryl installed there is an option in the Beryl Settings Manager in the Desktop Section called Widget Layer.

Basically if you click the + sign on the right and write cairo-clock it makes the dock a widget. (Don't forget to tick the Widget Layer Box)

It makes the Dock as a widget and therefore hides it under windows.

How that was of some help \\:D/

Glad to help

--Will--

---

### Post by acdc_au on 2008-06-18
Hi!

I found out (from cairo-dock --help:)), that if you start cairo-dock with the -n or -t flag, other windows will cover it.
So try this:
```
cairo-dock -t
```

This is because this way the window manager will treat it as a toolbar (-t) or as a normal window (-n)

Hope this helps.

---

### Post by fabounet on 2008-06-19
these options are almost deprecated since the 1.6.0 (means since yesterday ^_^), the dock can stay behind other windows and automatically popup in front of them when you place your mouse on the edge of the screen.

The Compiz's widget layer is particularily convenient to put the Cairo-Dock's widgets on.

---

### Post by calgarc on 2008-10-29
very simple close cairo-dock

then push alt+f2 and type "cairo-dock -t"

---

### Post by 080801jk on 2008-10-30
Servants of the Betrayer, the latest expansion for the World of Warcraft Trading Card Game, wow goldintroduces new sub-[**world of warcraft gold**](http://www.oofay.com/)factions, new types of allies, and brand-new abilities for your deck. The 246-card expansion also includes new Loot cards: Papa Hummel's Old-Fashioned Pet Biscuit, the Personalized Weather-Making Machine,wow gold and the X-51 Nether-Rocket Thundgot [** buy wow gold **](http://www.oofay.com/)posted the latest schedule for the 2008 Arena Tournament:Phase 1 - The Practice Phase ? Currently active and completes on April 23, 2008[**cheap wow gold**](http://www.oofay.com/)There is no penalty for changing your team and you are free to move teams around.At the end of this phase all arena team ratings will be reset to 1500 during maintenance.Phase 2 - The Competition Phase - Active from April 23, 2008 to May 7, 2008Every team will be reset to a 1500 rating and official rankings begin.There will be a 150 team rating penalty for any player added to an arena team.[**cheap wow gold**](http://www.oofay.com/)At the end of this phase all arena teams will be locked down and players will not be able to switch characters from arena teams.Registration will also close at the end of this phase.Phase 3 ? The Final Phase ? Active from May 7, 2008 to May 21, 2008Registration is closed for this phase of qualification.[**world of warcraft gold**](http://www.oofay.com/)Players are no longer allowed to switch arena teams during this phase.

---

