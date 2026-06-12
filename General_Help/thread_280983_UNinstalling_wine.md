---
title: "UNinstalling wine"
date: 2006-10-20
forum: General Help
---

### Post by weird_c00kie on 2006-10-20
bit of a weird question, but... how can i uninstall Wine?

i think something went wrong with the installation and it's not running properly. it worked fine last time i installed it, but now whenever i click any button which brings up a folder navigation window, it crashes.

for example, if i enter winecfg and click "add application", it crashes and quits on its own
similarly, if i run a program through wine, if i click anything which brings up a window to browse the drive with, it crashes.

i don't know if reinstalling it would fix it, but it's the only thing i can think of. if you have any other suggestions, please offer them. if not, it would be greatly appreciated if you could just tell me how to remove it completely from my system so i can then reinstall it and see if it works better :)


thanks in advance for any help

---

### Post by frogotronic on 2006-10-20
> **weird_c00kie said:**
> bit of a weird question, but... how can i uninstall Wine?

i think something went wrong with the installation and it's not running properly. it worked fine last time i installed it, but now whenever i click any button which brings up a folder navigation window, it crashes.

for example, if i enter winecfg and click "add application", it crashes and quits on its own
similarly, if i run a program through wine, if i click anything which brings up a window to browse the drive with, it crashes.

i don't know if reinstalling it would fix it, but it's the only thing i can think of. if you have any other suggestions, please offer them. if not, it would be greatly appreciated if you could just tell me how to remove it completely from my system so i can then reinstall it and see if it works better :)


thanks in advance for any help



Use the SYNAPTIC PACKAGE MANAGER (SYSTEM>SYNAPTIC PACKAGE MANAGER)

Search for WINE

Select COMPLETELY REMOVE

Then use SPM to reinstall


good luck

---

### Post by jcrnan on 2006-10-20
cement head: no need to use caps lock like hell :P

weird cookie: you can also write this in the console:

sudo apt-get remove wine 

or if you want to remove any settings (and installed programs trough wine)  you can do a 

sudo aptitude purge wine

to then install it again you type

sudo apt-get install wine

:)

---

### Post by CatKiller on 2006-10-20
An easy way to get rid of the configuration and start again is to use ```
rm -rd .wine
```This will remove the ~/.wine directory that holds the configuration and pretend C: drive. **winecfg** will then create it afresh.

EDIT: I'm such a fool. Of course it's a directory :roll:

---

### Post by weird_c00kie on 2006-10-20
thanks for that guys :) it's all nice and removed now hehe

when i typed sudo apt-get install wine though, i get this:
> Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

and i didn't uninstall it through synaptic to begin with because when i search for "wine", it isn't in the list of results that come up (it shows me kftpgrabber, libwine, libwine-dev, tellico and winefish)

i'll just use the how-to that i found here:
[http://ubuntuforums.org/showthread.php?t=185557&highlight=wine](http://ubuntuforums.org/showthread.php?t=185557&highlight=wine)

it worked last time :)

thanks again :D

---

### Post by jcrnan on 2006-10-21
wine should be there. have you unlocked all repositories+apt-get update+apt-get update?

---

### Post by weird_c00kie on 2006-10-21
i could post my sources file if you want and you can have a look. i'm still very much a newbie, so i wouldn't know. i know i've added extra repositories, but i don't know which and what for exactly :p


for the record, i uninstalled wine, reinstalled it again and it still doesn't work properly :(

any ideas? it still crashes the same way it did before

---

### Post by CatKiller on 2006-10-21
> **weird_c00kie said:**
> any ideas? it still crashes the same way it did before

As far as I know, uninstalling a package doesn't remove its configuration from your Home folder. So if the problem previously was with your configuration, it will still be your problem now. You can still delete the .wine folder and have it recreated for you if you want.

---

### Post by weird_c00kie on 2006-10-22
isn't that what rm -rd .wine was meant to do?

---

### Post by CatKiller on 2006-10-22
> **weird_c00kie said:**
> isn't that what rm -rd .wine was meant to do?

Yes. You didn't say that you'd already done so.

Otherwise, I don't know why Wine is crashing for you. It could be many things, including but not limited to drivers, 64-bitness, configuration peculiarities and the spite of the gods.

---

### Post by weird_c00kie on 2006-10-23
spite of the gods sounds most likely heheh

---

### Post by weird_c00kie on 2006-10-23
i think i've worked out what was going on

whenever i tried to open a file browsing window which looked for anything other than the emulated C drive, it would crash.
only way i've found around it is to make sure that anything i want to open is in the C directory and then type out a full location for it, like C:/folder/folder/file.extension
how bothersome... at least it works now :)

---

### Post by bolt212 on 2006-10-23
I've been having major problems getting wine to work.  

i followed the guide posted here ==> [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606) . 

scroll down and read the entery with the banner "How To Install Wine so that World of Warcraft Works on Linux !"  (its the second entry i think)

well,  i followed that guide and it worked.  all the way down till i have to do winecfg

I get this error


err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
chad@chad-laptop:~$ winecfg
wine: creating configuration directory '/home/chad/.wine'...
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Failed to open the service control manager.
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
wine: '/home/chad/.wine' created successfully.
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!


i found this page,  i tried using sudo aptitude purge wine.     
then i did sudo aptitude install wine.  

i still get the same error.    I have a X11 folder when i do a file search,   i've done a ATI driver installation also.

i can't figure out whats wrong.  it seems the way i installed it the first time prevents me from completely removeing wine and trying again.

if i simply redo the steps listed in that guide i linked to,  it takes 1/10 of the time because all the directories are already there and stuff and i still get the same error.


Ugh,  this is so dang frustrating.  lol.

If it makes any differance,  i am using Kubuntu.

---

### Post by weird_c00kie on 2006-10-25
way out of my league.... heheh hopefully someone else can help :)

---

