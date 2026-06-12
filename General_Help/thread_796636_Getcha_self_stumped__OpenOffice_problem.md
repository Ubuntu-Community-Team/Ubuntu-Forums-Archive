---
title: "Getcha self stumped:  OpenOffice problem"
date: 2008-05-16
forum: General Help
---

### Post by TangledVeins1208 on 2008-05-16
Hi everyone, this is my first of a many posts I'll be doing here @ UbuntuForums.  Love the site, love the people.  

A little background:  I'm off the Windows crack.  Going straight.  This is my 6th month, so I think I've kicked the habit.  I weened myself with a Live CD of Mandriva, then after trying Ubuntu repartitioned my hard drive completely and began installing distros left and right.  I've got Ubuntu 8, Fedora core 8, Knoppix, and Mandriva between 2 hard drives now, and I just got an external Maxtor 200GB drive so we'll see what I can do with that.  Also I've put linux on my 2GB USB pendrive.  LOVE LINUX MAN! I'VE BEEN BURNING COPIES OF UBUNTU LIVE FOR MY CO-WORKERS AND PASSING THEM OUT LIKE CANDY!  I'M ALL OVER LINUX LIKE TINY TIM ON A SMOKED HAM! *euphoric*  *foams at mouth*  Calming down... and onto the problem.

I seem to have messed up a setting in my Presentation that has bled over to Writer. I couldn't find a category in the UbuntuForums that would encompass this, so I've posted it here in General Help hoping someone will have a resolution.

While I was in Presentation, I jacked around with the Master Slide and changed all slide backgrounds to red.  I finished my presentation (which I made for my best friend to usher her onto Ubuntu and turn her back to Gates)  and shut down the PC.  This morning I boot up, scratch my rear, and start OoO Writer and guess what- my background is red.  Writer doesn't have a "Master Slide" obviously, so I've no idea how to go about it.  I went back into Presentation and reset the Master Slide, just for grins, then went back to Writer and nothing changed after I logged off and logged back on.  SO I THEN, using Synaptic Package Manager, completely removed OoO Writer, OoO Presentation, OoO core, and reinstalled.  Booted up Writer after reinstallation... seeing red. 
 q0,0p
(------)
If you help this monkey, the world will make sense again.

---

### Post by Patb on 2008-05-16
Tangled, that problem arises from your personal OO settings, not the actual program.  It should disappear (along with all your OO macros, settings and templates!) if you rename your ~/.openoffice.org2/ directory.  Make sure that OO is not running first, including any quickstarter if you have one.  When you restart OO it will create a clean "settings directory" at ~/.openoffice.org2/.  I'm fairly sure there will be no red!  ;)  You can then go looking for your old templates and settings files if you want them (search on the OO forum site for their location if you need) and copy them back into the correct location within your new ~/.openoffice.org2/ directory.  One of them might be causing the red, so keep backups of any files you overwrite.  

Cheers, Pat.

---

### Post by tact on 2008-05-16
Hey there...  I tried to duplicate what you did...  But no success.

I just opened up any presentation, changed the master slide background to blue and sure enough all slides in that presentation had a blue background.

Other presentations all had their normal backgrounds.  Opening up a document had the normal white background (or "none") etc as one would expect.

Interested what you did change.

Anyways...  as the previous poster wrote...  you can close all instances of openoffice and delete the config directory that you will find "hidden" in your home directory.   No need to reinstall OOo.  Next time you start OOo it will recreate your personal settings folder clean and new.

Since you are still in that ecstatic "honeymoon" phase with linux I'll give you a tip:
One of the very cool things about linux is that most applications behave as you have found with OOo. 

Its kinda a default that programs toss all user configs into their own folder/file hidden in the user's home folder. 

Its very cool because...  if you back up your home folder someplace off your HDD - you can even reformat, reinstall the OS, then restore your home folder to get back all your files etc...  with the PLUS - all your program settings are also all restored.   No need to reconfigure your email application, etc etc etc...

Its also cool because - if you manage to screw up your program's settings and want to start clean (as you did with OOo)..  you dont need to do the windows thing (uninstall and reinstall the program).   You just the settings folder/file inside your home folder.

---

