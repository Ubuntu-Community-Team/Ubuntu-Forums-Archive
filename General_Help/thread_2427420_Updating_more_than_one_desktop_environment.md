---
title: "Updating more than one desktop environment"
date: 2019-09-22
forum: General Help
---

### Post by michaelharden1a on 2019-09-22
I just added kubuntu desktop environment to my main Ubuntu machine running Ubuntu 19.04 gnome environment, I did this to see if KDE would perform faster than Gnome was doing.  My question is since I have the computer running both environments.  When it comes time to upgrade to 19.10 will both environments get upgraded or just one will?  I was planning to if it were possible to keep both installed and see if the performance of gnome improved any with the 19.10 update and then choose which one gnome or kde I wanted to use as the main driver then remove the one I did not need.  Earlier at one point I heard that a new gnome was coming out and that I could test it out before Ubuntu gnome was updated I installed gnome shell on the machine, that shell never got updated when Ubuntu was, and considering that it was not an environment installed using apt-get install kubuntu-desktop or xubuntu-desktop, etc it was logically not updated, in sorry for the extremely long winded question but I was just wondering.

---

### Post by ajgreeny on 2019-09-22
> **michaelharden1a said:**
> I just added kubuntu desktop environment to my main Ubuntu machine running Ubuntu 19.04 gnome environment, I did this to see if KDE would perform faster than Gnome was doing.  My question is since I have the computer running both environments.  When it comes time to upgrade to 19.10 will both environments get upgraded or just one will?  I was planning to if it were possible to keep both installed and see if the performance of gnome improved any with the 19.10 update and then choose which one gnome or kde I wanted to use as the main driver then remove the one I did not need.  Earlier at one point I heard that a new gnome was coming out and that I could test it out before Ubuntu gnome was updated I installed gnome shell on the machine, that shell never got updated when Ubuntu was, and considering that it was not an environment installed using apt-get install kubuntu-desktop or xubuntu-desktop, etc it was logically not updated, in sorry for the extremely long winded question but I was just wondering.
Having two DEs on a single OS and then removing the one you don't want, following testing both, is a nice theory but unfortunately not so simple as it sounds.

See the information in this post in the sticky thread on DEs, and the link it contains to Tips & Tricks.
[https://ubuntuforums.org/showthread.php?t=2415676&p=13848099&viewfull=1#post13848099](https://ubuntuforums.org/showthread.php?t=2415676&p=13848099&viewfull=1#post13848099)

You can probably continue with the two DEs on your system without huge problems other than duplicate file managers, text editors and other applications and utilities crowding the menu system of the OS, but that will not normally slow the system down as can happen in Windows with its huge registry system that gets larger and larger , slowing the OS.

I suggest that having added the kubuntu desktop, you use it as it is for a while, make your decision of which DE you prefer and then next time you install, choose your preferred DE, and stick with it.  It will make for much more smooth running.

PS:
When you carry out an update fom one OS version to the next, all packages installed, including both DEs if you have two, will be updated.
How smoothly that will occur, is something that I can not comment on as it's something I have never done; I have always clean installed, which in my opinion is better method of installation.

---

### Post by deadflowr on 2019-09-22
> My question is since I have the computer running both environments. When it comes time to upgrade to 19.10 will both environments get upgraded or just one will? 
All software gets updated upon any release upgrade.

---

### Post by michaelharden1a on 2019-09-22
So both KDE plasma will be updated along with Gnome? If so then that will allow me to see if Gnome gets better I doubt it and KDE does such a great job that I probably will end up removing Ubuntu-gnome de after the 19.10 upgrade.  Thanks again

---

### Post by deadflowr on 2019-09-22
You're better off just reinstalling Kubuntu then.
If you like it why waste your time on something else that *might* get better?

---

### Post by ajgreeny on 2019-09-24
> **deadflowr said:**
> You're better off just reinstalling Kubuntu then.
If you like it why waste your time on something else that *might* get better?

^^ +1 ^^
And as I said in post #2, it is almost impossible to remove a manually installed DE after the action.

For example, you may not be able to search for and then remove all packages with **gnome** in their name, as some of those may be dependencies of Kubuntu; I have not used Kubuntu for many years so I may be wrong about that but it will certainly not be an easy task.

---

