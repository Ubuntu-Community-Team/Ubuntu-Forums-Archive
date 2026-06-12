---
title: "awn freeze"
date: 2008-07-06
forum: General Help
---

### Post by jesse c on 2008-07-06
I have compiz and awn on my computer which has been fine up to a minute ago.I have problems with the newest Google Earth beta and in forums somebody talked about turning off compiz,so i tried to do that but cant figure out how to turn it off.Thats not my big problem though,it seems that somehow i screwed up my awn settings.now when i exit a window the awn icon on the toolbar starts spinning and then freezes and wont respond to mouse.Also if i go into Applications and click on awn a new dock appears on top of the existing frozen dock also i just now noticed that my firefox icon is not on the dock.Any ideas on what i screwed up?

---

### Post by jesse c on 2008-07-06
as a follow up i uninstalled awn by synaptic and reinstalled with same problem so i now uninstalled it again and am leaving it off  till i get some ideas. oh by the way compiz seems to still work fine(cube and fire wipe etc.)

---

### Post by pietjanjaap on 2008-07-06
Monday, April 14, 2008
Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager

---

### Post by jesse c on 2008-07-07
Pietjanjaap ,thanks for the help with the compiz situation but im still stumped on what i did to my awn dock.Even a new install has the same freeze problem and i dont remember changing any settings when searching for the compiz solution myself since i couldnt find anything to change but obviously i did.

---

### Post by serfcx on 2008-07-07
Can't  realy help but I have exactly the same problem

---

### Post by moonbeam on 2008-07-07
The awn freezing is probably related to the broken packages that were recently uploaded to hardy-proposed.

See:  [http://ubuntuforums.org/showthread.php?t=849005&highlight=awn](http://ubuntuforums.org/showthread.php?t=849005&highlight=awn)

---

### Post by jesse c on 2008-07-07
SOLVED thanks moonbeam,that was the problem,i guess i had downloaded the bad awn update and didnt connect that to the start of the problem.Following the link and downgrading awn and libawn did the trick,but now my update icon stays on telling me of libawn update available but ill live with that for now

---

