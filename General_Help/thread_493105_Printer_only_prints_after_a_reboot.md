---
title: "Printer only prints after a reboot"
date: 2007-07-05
forum: General Help
---

### Post by altonbr on 2007-07-05
It appears my Brother MFC-8440 keeps and holds the queue from anyone and everyone that has sent a job along, but it doesn't seem to print.

[http://localhost:631/](http://localhost:631/) has this beside the MFC-8440 printer:
> "Printer not connected; will retry in 30 seconds..."

It's odd because some sort of error occured, so I delete my printer, rebooted, re-added it and it didn't work (all using gnome-cups-manager).

I then deleted my printer, changed my configuration file to the default, then changed some networking options in [http://localhost:631/](http://localhost:631/) and it still didn't work.

All of these time, the printer was still accepting jobs. Upon a reboot, it would then print all the requested files. Since this server is also my desktop, this isn't acceptable.

I've attached my two configuration files.

I looked at the access, error and page logs but they don't look suspicious at all. I can't remember what it was that stopped the printer from working, sorry.

---

### Post by beerorkid on 2007-07-05
this was happening to me in edgy.  It was an USB Canon printer.  Pulling the USB out and then putting it back in would get it to print.  Not the best fix, but it worked.

No issues in feisty.

---

### Post by altonbr on 2007-07-06
Yeah, that doesn't seem to help.

I've restarted cups through the terminal and am looking for a way to reset USB ports, would work?

Also: It only seem to begin printer when the computer is logging INTO my account. Usually services begin at the login window, but this seems dependant on my user account and the queue it's holding.

---

### Post by BruisedQuasar07 on 2007-10-22
I think this is a common problem in Suse as well as Ubuntu. I have this problem

with a HP psc 1310 series printer. If you go to System > Administration >
Printing and right click on your printer icon, then click job, you will
probably find your print job (s) listed with "stopped" at the end of the line.

I discovered the same thing you have. A complete reboot & clicking on print
in some document may print the que but what works best is to remove the
printer icon, reboot, repete the Add (install) printer process.

Since I have always considered any PC a tool and not my main focus in life (I am glad for the less than 1% of people who do enjoy spending a huge 
chunk of their time with PCs) I follow a "keep it simple stupid" method. 

I only spend so much time a week on figuring out certain problems and
do simple work arounds in the mean time. I got back to the Printer
problem yesterday. Here is what I found in the time I allotted. What seems
to be the problem is we do not have specific manufacturer drivers. A couple former top printer makers cooperate, Hewlett Packard and Epson. A few
more provide limited (just in case Linux hits more desktops) cooperation.

There is a group that keeps up with the specific printers that work best
with Linux (and other free, OpenSource systems. Consider buying you
printer according to this list, rather than buy any printer that strikes your
fancy. Start Here [http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)

sourceforge.net and the Ubuntu Documentation site: help.ubuntu. com
look for printing & faxing, click and then look for linuxprinting.org

Or, go directly to linuxprinting.org

Also go to Ubuntu Wiki's Printer Page. 

It looks to me the problem is our print utility goes to "stopped" on reboot.
I did was not aware of the problem for a few weeks as I did not reboot or turn off my psc 1310 all-in-one printer. When I reboot the printing utility (cups, I think) is set to "stopped". 

Some users claim resetting it to "pause" works but a more permanent fix is unclear to me at this point. It seems to involve going into Cups and 
entering some code but the advice I found involves a printer series the 
three of us do not have. 

The Absolute Beginner team should address this problem so newbies do
not have to read a mass of data before they find a solution. As it stands, 
getting wifi running is so obscure it runs many away from Linux. I think
printing problems runs off people who invested time into migrating
to Linux. Forget much hyped, expensive books like Beginning Ubuntu
Linux and the other huge book Linux Bible. Neither one, like the
'Printer' "How To(s)" seem, even aware of this problem 

Their remains a serious communication and teaching problem in the
Linux community. So-called expert manual writers present themselves
as knowing more, even about specific Linux Distros, than they
really do. There is no more than a page or so in $35 to $50 huge
Linux books about printing or Wifi than you can find free online. 

I assure you this document print stopped is a very common problem, even
for people who use recommended HP and Epson printers. Any instruction
written by a so-called expert or power user should include the "stopped"
no print problem but none do. 

Being about to get your fav distrobution up and running and doing what
you want it to do does not make you an expert. Linux literate maybe but
certainly not expert. 

We will have to invest time tracking down sites where this specific problem is acknowledged and addressed. 

--Bruised

---

