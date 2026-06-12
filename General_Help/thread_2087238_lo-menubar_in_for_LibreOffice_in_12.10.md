---
title: "lo-menubar in for LibreOffice in 12.10"
date: 2012-11-23
forum: General Help
---

### Post by MorrisseyJ on 2012-11-23
Hi, 

I am a heavy LibreOffice user and really struggling with all the bugs that have arrived with the incorporation of global menus in 12.10.  I have read in a number of bug reports which mentions that i should install 'lo-menubar' to get around these problems as this application worked better than the currently integrated global menus.

When i try to install 'lo-menubar' i get the message that there are unmet dependencies.  Looking at synaptic i see that installing lo-menubar means uninstalling both 'libreoffice-gnome' and 'libreoffice-gtk'. These seem like important elements and i don't want to break my system, or LibreOffice. 

Could someone tell me whether its safe to go ahead with the lo-menubar installation in 12.10? 

Thanks.

p.s. The bugs that i am experiencing are all catalogued elsewhere: 

1. HUD not working: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1061225](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1061225)
2. Menu items are sometimes not responsive: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1081886](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1081886)
3. Menu items not accessible: [https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/1059814](https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/1059814)

---

### Post by MorrisseyJ on 2012-11-27
In a fit of rage at not being able to 'save as' on a document and not being able to insert a footnote, i uninstalled both 'libreoffice-gtk' and 'libreoffice-gnome'. 

I am unable to install lo-menubar as it seems to be reliant on libreoffice-gtk, as well as wanting to remove it. 

So now i am without global menus and HUD functionality and have a nasty looking libreoffice interface, but the menus are responsive. 

If anyone has a more functional (global menus and HUD) and aesthetically pleasing solution, please let me know. 

Thanks.

---

### Post by vanadium on 2012-11-27
Global menus and LibreOffice unfortunatelly cannot be combined for the moment afaict. The lack of ability to use Alt+key combinatins to access the menu is a deal breaker for me. There is no way, currently, to have this working with the global menu for LO.

I worked around this issue removing global menu's (and HUD) altogether. this is an "aestetically pleasing" solution, as it provides for consistency between all applications.

What you could try as a more aestetical solution, is reinstall the libreoffice gnome integration, but then try to disable global menu's for libreoffice only. => EDIT: trying to work with the UBUNTU_MENUPROXY to disable the global menu on a per program basis does NOT work with stock libreoffice. I currently do not know of a way to disable global menu's without breaking the other gnome integration in 12.10.

---

### Post by MorrisseyJ on 2012-11-28
Thanks vanadium,

I quite like using the HUD where i can. What i don't understand here is why i could run lo-menubar and have HUD working under 12.04, but not 12.10. 

Do you know if i can revert back to the version of LO that i was using in 12.04, before the attempt at global menu integration happened, and have it working with lo-menubar?

Thanks,

j

---

### Post by vanadium on 2012-11-28
I am no sure. It is certainly possible to install an older libreoffice version on your 12.10 system: uninstall the version that is there, and install from a download obtained from libreoffice.org. lo-menu on 12.10 might be installable with that version installed, but I do not know for sure.

---

### Post by MorrisseyJ on 2012-11-28
Thanks vanadium, 

I'll give it a try when i have a spare hour, and post results. 

j

---

### Post by vanadium on 2012-11-29
> **MorrisseyJ said:**
> Thanks vanadium,

I quite like using the HUD where i can. What i don't understand here is why i could run lo-menubar and have HUD working under 12.04, but not 12.10. 
It would be nice if you could try and post back here. In the last OOo versions, the global menu support is incorporated in the gnome-integration. In previous versions, the global menu support was provided through the lo-menubar package.

In a default Ubuntu 12.10 install, there is a dummy lo-menubar package installed by default (apparently temporarily needed for upgrades). If you remove that, you cannot install again: upon trying to reinstall it, it appears that the "real" lo-menubar package is called upon, but that gives the following error:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lo-menubar : Depends: libreoffice-gtk but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by MorrisseyJ on 2012-11-29
> It would be nice if you could try and post back here.Will do.

> In a default Ubuntu 12.10 install, there is a dummy lo-menubar package  installed by default (apparently temporarily needed for upgrades). If  you remove that, you cannot install again: upon trying to reinstall it,  it appears that the "real" lo-menubar package is called upon, but that  gives the following error:
   
    ```
 Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:  The following packages have unmet dependencies:  lo-menubar : Depends: libreoffice-gtk but it is not going to be installed E: Unable to correct problems, you have held broken packages
```. 
Confusingly, if you then install libreoffice-gtk and try and install lo-menubar it tells you that you need to uninstall libreoffice-gtk. 

I don't really understand this, but will post back on reinstalling an older version. 

j

---

### Post by Radical Thought on 2012-12-17
I have the same kind of problems with LO. Is there already a bug report on this?

---

### Post by vanadium on 2012-12-17
[http://ubuntuforums.org/showpost.php?p=12368928&postcount=1](http://ubuntuforums.org/showpost.php?p=12368928&postcount=1)

---

### Post by MorrisseyJ on 2012-12-17
Hi, 

I started looking at this and then saw that i needed to compile from source. I started doing this (using the readme) but got as far as installing the desktop integration and got stuck when i had to remove libreoffice-core, as it contained libreoffice-bundled, which conflicted with libreoffice-debian-menus.

When i went to remove libreoffice core in synaptic i saw that i was removing a few other things as well - notably python stuff which has broken my system previously. 

I thus got scared and left it. Sorry not to have been able to push through with this, its my first time compiling from source and it just seems too much for me to do this with a programme that is so central to my needs and also requires the uninstallation of a another, later version, of the programme. 

If anyone with more confidence fancies having a go at this, i'd welcome any lessons learnt. 

Now i am off to learn how to compile something from source...

j

---

