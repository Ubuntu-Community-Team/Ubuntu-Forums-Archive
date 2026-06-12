---
title: "Trouble installing samba GUI"
date: 2015-03-24
forum: General Help
---

### Post by KayeNg on 2015-03-24
Hi guys.  This is what I did. 

1.  sudo apt-get install samba
      ---- having trouble accessing shared files on Lubuntu system from Windows XP, so

2.  sudo apt-get remove samba (or something like that)
     ----- the directory etc/samba was still there, so I used sudo to open the file manager, then deleted that directory.  It was deleted without going to the TRASH.

3.  Followed someone's advice to install the samba GUI, system-config-samba.   Installed it through Synaptic Package Manager.

4.  When I open it, a window appears for a split second only.  GUI could not be opened.

5.  Uninstalled it using Synaptic.  Reinstalled.  Same thing.

6.  Uninstalled and reinstalled using Software Center.  Same thing.

I feel it has something to do with installing the non-GUI samba thru [sudo apt-get install samba], then uninstalling, then installing the GUI version.  
Because a similar thing happened to me with ndiswrapper.  Installed the non-GUI, uninstalled, installed GUI, then GUI won't open.  

With the ndiswrapper, I ran out of ideas so I just reinstalled the entire Lubuntu OS, then ndiswrapper worked.  But please don't suggest that I do the same, I'm tired of reinstalling the entire OS just to fix one problem, it is overkill.

I'm thinking of going to Synaptic, type in "samba" in the search bar, remove everything that has to do with samba that is currently installed, THEN installing the GUI samba.  

What do you think?

---

### Post by dino99 on 2015-03-24
might be of some help
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)
[http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7](http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7)

---

