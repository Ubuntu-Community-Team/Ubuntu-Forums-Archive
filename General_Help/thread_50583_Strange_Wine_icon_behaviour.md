---
title: "Strange Wine icon behaviour"
date: 2005-07-20
forum: General Help
---

### Post by ShaneR on 2005-07-20
I installed wine for the soul purpose of running two very small programs I use in conjunction with my dialup service (Internet Call Manager and Dialup accelerator).  Both work as I expect.

The stange thing in Ubuntu(Gnome), was that when they started up, instead of the icons for the programs going to the systray, 2 small boxes were placed on the desktop.  By small, I mean my cursor had to be over one certian pixel to access the menus for the programs...very annoying.  But, I learned to deal.

However, this afternoon I started Kontact while in Gnome and the 2 icons suddenly appeared in the systray as they should.  I figured out they did so as soon as the KOrganizer Alarm Daemon started.

Anyone know why? I'm guessing that when the daemon starts, it also starts something allowing the icons to go to the systray...not sure what though.

Oh well....just wondering :)

---

### Post by gn0me on 2005-08-09
Yeah.  I guess a system tray thing could be written to make icons go into the system tray panel thing, but that would be writing something seperate from WINE and actually writing a GNOME panel script.

When the wine environment loads it makes a global system tray and that's what you're seeing.  It's a little buggy, yeah.. but it still sort of works.

Not sure why it wouldn't then suddenly did.

---

### Post by Kimm on 2005-08-10
It works in XFCE4... perhaps there is something you can use from there in gnome?

---

### Post by Chris Tucker on 2005-11-14
AHAAAAAAAA!!!!!!!!!
Finally! the solution i have been looking for!
Amazingly you're even using one of the same programs that has been annoying the hell out of me.. Internet Call Manager.. its a major pain in the arse but at least its something untill they get highspeed in my area..

this problem has been pestering me to death for a little over a year now with gnome.. worked fine in kde..

Well i snooped around a bit with top | grep chris   to see what launcher name is attached to that KOrganizer Alarm Daemon, its korgac

might aswell post a quick howto for installing Internet Call Manager in Ubuntu .. for anyone else aswell as myself should i forget

First off enable the other repositories in your apt system... look around for how to do that.

i used synaptic to grab the wine package.. as  " sudo apt-get install wine " returns an error, getting it from command line requires a name thats not so easy to remember. just search for wine with synaptic or your favorite package manager.

then, grab the InstallICM.EXE file from the ISP website

type this: wine /path/to/your/InstallICM.EXE
(note, you may have to run winecfg and set a windowed resolution for installicm.exe, i havent tried it without doing that yet)
click yes yes yes... whatever you would in windows..
exit ICM
if you left the install path alone your command to run icm should be " wine /home/yourusername/.wine/drive_c/Program\ Files/Internet\ Call\ Manager/ICM.EXE  "
run this to make sure it works, note you wont see your systray icon yet.. then close icm again.

sudo apt-get install korganizer

then.. from the ubuntu menus go System -> Prefrences -> Session   then choose startup programs tab.
add an item .. command  " korgac "  with order of 1
add another item .. command " wine /home/yourusername/.wine/drive_c/Program\ Files/Internet\ Call\ Manager/ICM.EXE " with order of 2
log out and back in and you're set!

---

