---
title: "wine menu in gnome"
date: 2007-05-23
forum: General Help
---

### Post by zorkerz on 2007-05-23
I was attempting to change a launcher in the wine menu under applications, but i messed up. When i hit revert it added wine in front of all of the items in the wine list. Ex. wine became wine-wine. This is only a minor annoyance but then i managed to delete the whole wine list and cannot get it back. I have tried reinstalling wine.

I feel kinda stupid about all this but in all fairness it is an odd system where properties of the main menu launchers cannot be viewed except through system->preferences->main menu
I think this makes little sense. It would be much easier if launchers could be dragged in and out without requiring a separate procedure.

Any ideas how i can get the menu back. What is the process that makes this in the first place?

---

### Post by zvacet on 2007-05-23
Open home directory>view>hidden files and you will find .wine folder.Uninstall wine with synaptic and delete that folder.Reinstall wine.

```
winecfg
```

---

### Post by zorkerz on 2007-05-23
I thought about doing this but i have many things installed in the .wine folder and would prefer not to loose them. Anyone know what folder/file specifically holds the wine menu settings in .wine?

Why do you say to use winecfg i believe the menu is added before configuring wine.
thanks

---

### Post by zorkerz on 2007-05-23
I just did exactly as you have said and then proceeded to reinstall all my programs (only games) again but the wine menu is still non existent. Thanks for the try. Any other ideas?
Im attempting to just make the menu myself. First i need to remember all the commands i was using and get the games to work again.
cheers

---

### Post by rushin_911 on 2007-06-03
Hi.

I had the same problem. I was able to find out that the wine menu entries are located at:

/home/(user)/.local/share/applications/wine/Programs

where (user) is your user name. I haven't figured out though how to put it back in the menu (you can do that manually if you just create new entries and copy the commands from the ones in this directory).

---

### Post by zorkerz on 2007-06-04
thank you rushin_911 this is just what i needed. I was trying to recreate the commands but sometimes they are not very obvious. This way i can just add them back manually quite easily. I wonder what happens to put them in the main menu originally. You would think there should be a way to do this again.
again thank you much
elias

---

### Post by FoolishGhoul on 2007-06-04
Has anyone else found their WINE icons scattered randomly through the menu system?

It seems really strange, when I was using Xubuntu I never had this problem, they were all arranged in a "Wine" folder.  Also when I go to the "Main Menu" setup utility I can't move them around.  Has my flu got so bad that I'm going crazy or am I just missing something?

If anyone has any good advice let me know!

---

### Post by chuong on 2007-06-06
You run "wineboot", wine menu with all installed Windows software will appear in the Applications menu.

---

### Post by zorkerz on 2007-06-07
> **chuong said:**
> You run "wineboot", wine menu with all installed Windows software will appear in the Applications menu.

This would be awesome. Unfortunately it did not work for me. Here is the output from the command if anyone is interested.

```
wineboot
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\windows\profiles\zorkerz\Start Menu\Programs\Starcraft\Starcraft.lnk
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\windows\profiles\zorkerz\Start Menu\Programs\Starcraft\Starcraft Readme.lnk
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\windows\profiles\zorkerz\Start Menu\Programs\Starcraft\Starcraft Help.lnk
fixme:shell:DllCanUnloadNow stub
err:menubuilder:InvokeShellLinker failed to extract icon from L"c:\\Program Files\\Starcraft\\BroodUnits.doc"
fixme:shell:DllCanUnloadNow stub
err:menubuilder:InvokeShellLinker failed to extract icon from L"c:\\Program Files\\Starcraft\\Readme.hlp"
fixme:shell:DllCanUnloadNow stub
err:menubuilder:InvokeShellLinker failed to extract icon from L"E:\\Support\\Support.htm"
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\windows\profiles\zorkerz\Desktop\Steam.lnk
err:wineboot:runCmd Failed to run command L"" (2)
err:wineboot:ProcessRunKeys Error running cmd #0 (2)
```

---

