---
title: "Removing evolution"
date: 2005-10-31
forum: General Help
---

### Post by peterthewolf on 2005-10-31
While I can install and use thunderbird for my mail with no problem I cannot delete evolution from the system. What makes evolution so sacrosanct.

---

### Post by LorenzoD on 2005-10-31
I've never tried removing Evolution since I use it, but I don't think removing Evolution itself should be a problem. Gettting rid of Evolution Data Server, on the other hand, might not be as trivial.

---

### Post by peterthewolf on 2005-10-31
Sorry why should getting rid of Evolution Data Server be so bad after all its only an email program so what else should depend on it. If you cannot get rid of it then you end up with the bloated windows scenario.

---

### Post by LorenzoD on 2005-10-31
Well, the clock applet does query evolution-data-server to present you with your task list and upcoming appointments. The deskbar applet, which may make it into the next Gnome release also queries e-d-s. 

But I do agree that you should be able to remove components of the desktop that you don't want.

---

### Post by Kyral on 2005-10-31
sudo apt-get remove evolution evolution-data-server

---

### Post by dom on 2005-10-31
try to remove evolution via synaptic and it wants also to remove :
+evolution-exchange
+evolution-plugins
+ubuntu desktop

try to remove the evolution data server and it wants also to remove :

evolution
evolution-exchange
evolution-plugins
gnome-applets
gnome-applets-data
gnome-control-center
gnome-panel
gnome-session
gnome-terminal
nautilus
ubuntu-desktop


surely this is just mad ?

will using apt manually do this also ?

---

### Post by dom on 2005-10-31
i just found a "no act" option for apt-get, it sure looks like it's not possible to remove evolution on it's own-ee-oh

i don't know about removing all those gnome pieces..........?

i guess it just has to hang around.

sudo apt-get -s remove evolution evolution-data-server
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  evolution evolution-data-server evolution-exchange evolution-plugins gnome-applets gnome-applets-data
  gnome-control-center gnome-panel gnome-session gnome-terminal nautilus ubuntu-desktop
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
Remv ubuntu-desktop [0.80]
Remv evolution-plugins [2.4.1-0ubuntu7]
Remv evolution-exchange [2.4.1-0ubuntu1]
Remv evolution [2.4.1-0ubuntu7]
Remv nautilus [2.12.1-0ubuntu1]
Remv gnome-terminal [2.12.0-0ubuntu2]
Remv gnome-session [2.12.0-0ubuntu1]
Remv gnome-applets [2.12.1-0ubuntu1] [gnome-applets-data ]
Remv gnome-applets-data [2.12.1-0ubuntu1]
Remv gnome-panel [2.12.1-0ubuntu7]
Remv gnome-control-center [1:2.12.1-0ubuntu2]
Remv evolution-data-server [1.4.1-0ubuntu3]

---

### Post by aysiu on 2005-10-31
[QUOTE=dom]try to remove evolution via synaptic and it wants also to remove :
+evolution-exchange
+evolution-plugins
+ubuntu desktop[/quote] There's nothing wrong with removing these guys. I have, and, as far as I can tell, there's no harm done.

> 
try to remove the evolution data server and it wants also to remove :

evolution
evolution-exchange
evolution-plugins
gnome-applets
gnome-applets-data
gnome-control-center
gnome-panel
gnome-session
gnome-terminal
nautilus
ubuntu-desktop
 I wouldn't do this, however.

---

### Post by Foaming Draught on 2005-10-31
Same here, I use Thunderbird for mail (who wouldn't?) and JPilot for my desktop PIM. When I tried to remove bloated, slow, Palm-unfriendly Evolution, I got warned off by Synaptic. So I've made a virtue of necessity by one-time synching my mobile phone to the Evolution Address Book and adding Palm contacts, so that the desktop address applet and Phone manager drop-down boxes work. These latter two applications are so useful that it's worth keeping the rest of the useless suite idle on disk.

---

### Post by RAOF on 2005-11-01
Evolution-Data-Server has actually become a pretty much core piece of gnome, IIRC.  It's used as a generic data-storage system, I believe, which just happened to start out as a part of evolution.

---

### Post by peterthewolf on 2005-11-01
As pointed out to remove evolution you have also to remove much else. Not being afraid to try I did result no system the pc just would not boot. Had to reinstall breezy so I would say leave be,

---

### Post by dom on 2005-11-02
no arguing with that !

:)

---

### Post by Riverside on 2005-11-02
Why remove it?  I don't use it, and simply remove its icon from the Gnome panel.

---

### Post by casperl on 2005-12-06
I really want to purge the last vestige of evolution from my system!

The reason is simple:

I would like to use J-Pilot as my one and only and default Palm Application on my system.  As long as evolution is present it cannot be done.  Somewhere, somehow is an evolution task that grabs the palm as it's teritory.

I had this problem on 'hoary' and vowed that I will install an 'breezy' fresh on a new machine, without evolution.  But Evolution is back.  I have not yet started it on Breezy, but it has grabbed control of the Palm device.

How do I remove it?

On a side note, the new direction in email is not the classical 'Outlook' style copied by Evolution, but rather the web interface of OperaMail or GMail.

Now, IF ONLY, I could get rid of evolution I could use the address book in J-Pilot.
:confused:

---

### Post by IanLowe on 2005-12-06
[QUOTE=casperl]
On a side note, the new direction in email is not the classical 'Outlook' style copied by Evolution, but rather the web interface of OperaMail or GMail.
[/QUOTE]


I can appreciate that you might want to remove Evolution in your own situation, but as someone who pretty much lives by email (as many as four hundred in a typical day)... webmail is a toy, for a little convenience on the road.

Evolution is (imo) the best thing to happen to desktop linux in a long time... the problem is that even in the current versions, it's calendaring is still not good enough.

THere's a long term thread running about "reasons why you keep dual booting". for me it's Outlook 2003. to win the business desktop, Linux needs a powerful business time and information scheduling tool - and Outlok is a brutally hard act to follow.

I'm even considering getting a copy of Crossover Office just so I can keep running Outlook... and really, I'd much rather use a FOSS tool in it's place. :(

---

### Post by paulvandenberg on 2005-12-06
Perhaps, Evolution Data Server should be renamed GNOME Data Server since it used for more than Evolution now.

Paul

---

### Post by dom on 2006-03-01
whatever about the advantages of having evolution available and working will as an email client and incorporated with calendar etc,

surely it's not the case that it should be imposed, such that removing it renders a system unusable.

ps, is anybody here using ubuntu with KDE ?

is evolution in as much control there ?

---

### Post by RAOF on 2006-03-01
[QUOTE=dom]try to remove evolution via synaptic and it wants also to remove :
+evolution-exchange
+evolution-plugins
+ubuntu desktop
...[/QUOTE]
You **can** remove (just) evolution.  The "evolution-exchange" & "evolution-plugins" packages are the Microsoft-exchange access plugin & various other evolution plugins, respectively.

The "ubuntu-desktop" package is a metapackage - it doesn't contain anything, it just depends on all of the default Ubuntu software.  That's so you can install a default system with "apt-get install ubuntu-desktop".  There's no real harm in removing it.

---

### Post by mcilwraith on 2008-01-28
Having evolution data server hooked into Ubuntu for such things as time keeping is like Windows forcing explorer and Media Player as necessary components in oder to operate.

---

