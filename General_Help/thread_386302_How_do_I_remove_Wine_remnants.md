---
title: "How do I remove Wine remnants?"
date: 2007-03-16
forum: General Help
---

### Post by Handssolow on 2007-03-16
I am unable  to remove all traces of Wine and a Windows application.

I've bought a TOMTOM 910 satalite navigation system but as there's no Linux support on the CD, I've been playing around with Wine  and seeing if I can get TomTom Home running under Ubuntu. I have had some success, I was able to download but not install an update for the TT Home program but not download updates to the 910 unit. Next instead I downloaded the latest TT Home software from the website onto Desktop and using Wine ran the install. It then seemed that I was able to upgrade my 910 unit.

Having run two TomTom Home.exe files things look a bit untidy and I get the following

Applications>Wine>Programs>TOMTOM............>Uninstall TomTom HOME
.......................................................>TomTom Home>Remove TomTom HOME
.....................................................................................>TomTom HOME

It seems that I'm unable to remove the applications using with the Uninstall and get an error message if I use Remove. If I remove Wine with Add/Remove or Synaptic or Automatix2, the above lines are still showing Wine as an Application even though winecfg brings up nothing.

How do I remove these items from the drop down Application start menu.
Where would the TOMTOM HOME software have been installed in my Ubuntu file system when Wine was using it.

I'd like to do a fresh install of Wine and TOMTOM software after I've first cleaned things up from my previous experiments. I want to return to running this application full screen but it keeps defaulting to runnings in a smaller window.

---

### Post by pt123 on 2007-03-17
Have you tried using System>>Pref>>Menu Layout?

---

### Post by Handssolow on 2007-03-17
Many thanks that's cleaned up my applications list. The listing for Wine and the TOMTOM application has gone though Wine still appears as an option in Menu Layout.  I'm not sure if I've just swept things under the carpet. I'll see what happens when I reinstall Wine when I've some more time later in the day.

Where will my windoze application TomTom Home have gone within my Ubuntu file system and how might I remove any traces before I perform a fresh install.

---

### Post by gkiller on 2007-03-17
> **Handssolow said:**
> Many thanks that's cleaned up my applications list. The listing for Wine and the TOMTOM application has gone though Wine still appears as an option in Menu Layout.  I'm not sure if I've just swept things under the carpet. I'll see what happens when I reinstall Wine when I've some more time later in the day.

Where will my windoze application TomTom Home have gone within my Ubuntu file system and how might I remove any traces before I perform a fresh install.
Normally, all Wine files go to ~/.wine/

You'll find a drive_c directory there. This is your fake Windows drive with all installed files.

---

### Post by Handssolow on 2007-03-17
Thanks for the help.
I want to clean things up before doing a fresh install of Wine and TomTom Home.
I've removed Wine with synaptic but the .wine folder is still there. The windoze application TT Home isn't in the folder so I assume it's now gone. However, System>Preferences>Menu Layout still shows Wine as an option including the consequences of my installs of two versions of TT Home. 

I'm unable to delete these menu options with Menu Layout even though it's an right click option.

Any suggestions?
Should I delete the .wine folder and if so how?
How can I remove the old wine options from Menu Layout before a fresh install?

---

### Post by gkiller on 2007-03-17
> **Handssolow said:**
> Thanks for the help.
I want to clean things up before doing a fresh install of Wine and TomTom Home.
I've removed Wine with synaptic but the .wine folder is still there. The windoze application TT Home isn't in the folder so I assume it's now gone. However, System>Preferences>Menu Layout still shows Wine as an option including the consequences of my installs of two versions of TT Home. 

I'm unable to delete these menu options with Menu Layout even though it's an right click option.

Any suggestions?
Should I delete the .wine folder and if so how?
How can I remove the old wine options from Menu Layout before a fresh install?
Yeah you can delete the .wine folder. Although then all your wine settings will be gone. You could also try in a terminal:
```
apt-get remove --purge wine
```
That should also remove all configuration files.

To remove something from the menu right-click on the "Applications" Text and select "Edit Menus". Then you can delete there the appropriate entries.

---

### Post by Handssolow on 2007-03-17
Thanks gkiller.
I think I've removed Wine and it's configuration files. I understand that the .wine directory in /home/Handssolow/.wine was created after I installed wine and doesn't need to be removed. True?

Good news too, after many many goes at deleting the wine entries they suddenly disappeared. I right clicked on Application>Edit Menus as you suggested rather than System>Preferences>Menu Layout method. a Bug?

---

