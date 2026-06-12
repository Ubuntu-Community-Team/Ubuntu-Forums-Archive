---
title: "Blank Screen after Ubuntu 17.04 upgrade"
date: 2017-08-26
forum: General Help
---

### Post by richard7893 on 2017-08-26
Hello

I have tried to upgrade from 16.04 LTS to 17.04. Upon completion of the upgrade I tried to restart my computer as directed in the prompts. I had to hold the power button on my computer as the computer would not restart on its own and would stay on the Ubuntu splash screen (This is a separate issue altogether [https://ubuntuforums.org/showthread.php?t=2368074](https://ubuntuforums.org/showthread.php?t=2368074) I thought performing an upgrade might fix the power off problem). Anyways, when I power the computer back on, I am able to get to the purple screen that says "you must make a selection or the highlighted option will be selected in 10, 9, 8...".  When I select an option, all I get is a blank screen with a 'X' mouse cursor that I can move around. I am also able to right click though, and I get the list like 'New Folder, Paste, Select All etc.'. Once again the screen is blank though. I also notice that if I try to create a folder of the same name as one I had on my 16.04 version, the screen says 'A folder with that name already exists'. So the computer still has my stored folders & info, I guess, but I just cannot see anything! The screen remains blank other than when I right click and see the options as a result (New Folder, Paste, Select All etc,). Does anyone know how I can fix this?

---

### Post by Bashing-om on 2017-08-26
richard7893; Hello;

Fault isolation:
1) In the grub boot menu -> advanced options -> recovery : what results with booting up a recovery console ? ( graphics's driver issue ?)
2) Login screen -> guest user account : what results when booting up as the guest user ? ( user config issue ?)

[INDENT][INDENT]could be this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by richard7893 on 2017-08-27
OK. 

So when I follow suggestion 1), I select advanced options on the GRUB boot Menu. I attached a photo of the screen I get. Selecting 'resume Resume normal boot' brings me to a blank screen with a blinking cursor. 


I am not sure how to follow your instructions in suggestion 2). I do not get any options to login as a guest user account. Could you elaborate on how to explore this option so that I may give feedback?

---

### Post by Bashing-om on 2017-08-27
richard7893; Well.

Still do not know enough to say this is a system problem, a config issue in your home directory, or a graphic's driver issue .

At the recovery console, what results when choosing " fail safe graphic mode" ?
At the login screen in the login box; I expect that there is a drop down menu from the ubuntu icon within that box . 

Else, what results at the login screen - ctl+alt+F1 ? Can you activate a console interface - user name and pass word  ? From here if the CLI activates we can also see what we can learn .

[INDENT][INDENT]the process
[INDENT][INDENT][INDENT]of fault isolation
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

