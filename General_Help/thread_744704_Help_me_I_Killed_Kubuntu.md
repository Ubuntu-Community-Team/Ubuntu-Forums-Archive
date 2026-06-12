---
title: "Help me I Killed Kubuntu"
date: 2008-04-03
forum: General Help
---

### Post by yoshimitsuspeed on 2008-04-03
Ok I know this was dumb but here's what I did. 
I installed KDE4 over KDE3  When installing a KDE 4 update it asked me if I wanted KDE 3 or 4 to be the default and I selected 4. 
Kde 4 acted up and wouldn't let me type anything anywhere. 
I figured it was a glitch in a package or something so I uninstalled everything KDE4. I figured I would restart my comp and reinstall KDE4 and suprise it wouldn't start the window manager on restart. 
I signed into the terminal and typed kwin and it said something about not being able to start the server or something. 

What can I do to get it back online? 
I have another version of Kubunto on the same computer so I can go in through it to edit files or I could go in through the terminal, whichever is easiest. 
I am guessing I just have to reset KDE3 as the default but I don't know how.

---

### Post by Crafty Kisses on 2008-04-03
> **yoshimitsuspeed said:**
> Ok I know this was dumb but here's what I did. 
I installed KDE4 over KDE3  When installing a KDE 4 update it asked me if I wanted KDE 3 or 4 to be the default and I selected 4. 
Kde 4 acted up and wouldn't let me type anything anywhere. 
I figured it was a glitch in a package or something so I uninstalled everything KDE4. I figured I would restart my comp and reinstall KDE4 and suprise it wouldn't start the window manager on restart. 
I signed into the terminal and typed kwin and it said something about not being able to start the server or something. 

What can I do to get it back online? 
I have another version of Kubunto on the same computer so I can go in through it to edit files or I could go in through the terminal, whichever is easiest. 
I am guessing I just have to reset KDE3 as the default but I don't know how.
Hmmm, try the following at the Terminal:
```
startx
```
What happens when you do that?

---

### Post by zvacet on 2008-04-04
Maybe [this #2](http://ubuntuforums.org/showthread.php?t=744171&highlight=KDE4) can help you.

---

### Post by yoshimitsuspeed on 2008-04-04
Okay thanks.
Start X got me back into KDE3 and I reinstalled Kde4 however KDE3 is only partially functional.
It says several things like System, trash, and network have malformed urls. 
I checked them and I think they are right . Example system location is system:/ but when I click on the icon in dolphin it says malfored url.  The system Icon in my taskbar says it's empty. 

Oh and KDE4 still won't accept keyboard inputs lol.

---

### Post by yoshimitsuspeed on 2008-04-05
So does anyone  know how to get my system urls demalformed?

---

### Post by tubasoldier on 2008-04-05
delete the .kde and .kde4 directories underneath your /home/USER/ .

This will remove all configuration files and everything will reset to default. You should be able to select KDE4 or KDE3 from the login screen.

---

### Post by yoshimitsuspeed on 2008-04-06
> **tubasoldier said:**
> delete the .kde and .kde4 directories underneath your /home/USER/ .

This will remove all configuration files and everything will reset to default. You should be able to select KDE4 or KDE3 from the login screen.

This did fix kde 4 not accepting keyboard input so thanks. I also didn't heve kde 4 set up with extensive settings changes so no big loss. 
Kde 3 still has malformed URls so no change. Fortunatly I just renamed both files so I can keep my KDE 3 settings cause I have spent a lot of time customizing it. Thanks now KDE4 seems ok but KDE3 is my main workhorse.

 Any more ideas to fix the URL prob?

---

### Post by yoshimitsuspeed on 2008-04-07
Heeeeeeeeeeellllllllllllllllllppppppppppp meeeeeeeeeeeeeeeeeeee
I can't imagine this be the most unfixable situation out there.

---

### Post by anindya_m on 2008-04-07
Have you tried uninstalling kde3 completely (including config files) and reinstalling. Something might have been overwritten by the kde4 install...

---

### Post by yoshimitsuspeed on 2008-04-07
> **anindya_m said:**
> Have you tried uninstalling kde3 completely (including config files) and reinstalling. Something might have been overwritten by the kde4 install...

I'd hate to loose all my config settings, plus I am kinda afraid I might remove something KDE4 depends on and completely kill the system. 
I know enough to know I know little enough to know that  I would probably screw that up.

---

### Post by anindya_m on 2008-04-08
By config files I meant not your .kde but the systemwide config files (the --purge option in dpkg). Yes there is some risk that it may disable kde4, but then if kde3 is installed correctly again your config should just start working.

---

### Post by yoshimitsuspeed on 2008-04-09
Can I do that in synaptic PM or would I do it in the terminal?
Mind giving me some instructions? I am still pretty new at this.

---

### Post by anindya_m on 2008-04-16
You can do it from Synaptic. Just click on the package and choose "Completely Remove (including config files).

It is also possible with dpkg --purge from the terminal. However, since you are new I'd suggest using Synaptic.

---

### Post by yoshimitsuspeed on 2008-04-17
Thanks for your help. 
I installed kubuntu 8.x on another partition and now it's dialed in to be my pri os
I will try this when I get some time. 
Thanks again

---

### Post by anindya_m on 2008-04-17
You're welcome. Hope everything works properly :)

---

### Post by bouncingmolar on 2008-04-20
I've had this problem before i forget how i fixed it.

try installing konqueror

apt-get install konqueror

if that don't work try installing kdesktop

---

