---
title: "bottom toolbar"
date: 2019-01-22
forum: General Help
---

### Post by oneleded on 2019-01-22
while trying to figure out getting Thunderbird icon, to the bottom toolbar, i somehow got all icons on the left side of the toolbar. i would like to get it back to when some were on the left, an others are on the right. restore original. where can i find this at?, or how to do this? i aint picky

---

### Post by Dennis N on 2019-01-22
If you have Lubuntu 18.04, be sure the task bar (window list) has the 'stretch' box checked. If it's not, the panel items all 'collapse' towards the left.

---

### Post by oneleded on 2019-01-27
task bar (window) list, doesnt have a 'stretch' box to check. i did get my icons back to some on the left an others on the right as before by removing some of the panel applet's,,, until,, not having a stretch box to check, i thought maybe you meant spacer. so i added it, and checked it, now all icon's  are stuck on the left again.
when i right click on a desktop icon, my shortcut editor is not responding also..  i managed to delete some of the icons, firefox, for example, that i had on the task bar..
when i make a mess, i make a good one. lols..  Ed

---

### Post by again? on 2019-01-27
FYI you can set the panel back to system defaults by moving the user config files.
```
mv ~/.config/lxpanel ~/.config/lxpanel.bak
lxpanelctl restart
```

---

### Post by dragonfly41 on 2019-01-28
You might find that installing [docky]("http://www.go-docky.com/") is helpful to your workflow.

---

### Post by Dennis N on 2019-01-28
> task bar (window) list, doesnt have a 'stretch' box to check.

So far, you haven't disclosed what version of Lubuntu you are using. In 18.04, the Window List has the stretch option, in 18.10 it doesn't. In case you have 18.04, the attachment shows where the 'stretch' option is found and needs to be checked, as mentioned in post #2.

---

### Post by oneleded on 2019-01-28
> **Dennis N said:**
> So far, you haven't disclosed what version of Lubuntu you are using. In 18.04, the Window List has the stretch option, in 18.10 it doesn't. In case you have 18.04, the attachment shows where the 'stretch' option is found and needs to be checked, as mentioned in post #2.
18.04 LTS; sorry for that.

---

### Post by oneleded on 2019-01-28
> **guber2 said:**
> FYI you can set the panel back to system defaults by moving the user config files.
```
mv ~/.config/lxpanel ~/.config/lxpanel.bak
lxpanelctl restart
```
i copied that code and pasted it into the terminal. it is way better now.. 2 icons are over to the right, that dont matter, but the rest on the right are just fine, and im just glad to have as it is. thanks for the code.  ed
also, my missing shortcuts, firefox, an file manager PCManFM, were back, on 'Application Launch and Task Bar'. i wasnt sure what 'ALTB' was as i had already deleted those icons in my attempt, to restore my task bar. now i know. i also think i know how to get thunderbird on the list. we shall see, and if i mess up, some will learn. thanks for the help i get.  Ed

---

### Post by oneleded on 2019-01-28
> **Dennis N said:**
> So far, you haven't disclosed what version of Lubuntu you are using. In 18.04, the Window List has the stretch option, in 18.10 it doesn't. In case you have 18.04, the attachment shows where the 'stretch' option is found and needs to be checked, as mentioned in post #2.
i didnt read that right, when it was posted. my brain??  anyway when i add it and check the box, the icons move to the middle, an a get a double of firefox browser, when i click that icon,, an when i click on 'add/remove panel items' 2 of those show up in system tray also. thanks,  ed

---

### Post by oneleded on 2019-01-28
> **dragonfly41 said:**
> You might find that installing [docky]("http://www.go-docky.com/") is helpful to your workflow.
i installed docky from, 'Synaptic Package Manager' thanks

---

### Post by oneleded on 2019-01-30
> **oneleded said:**
>  i also think i know how to get thunderbird on the list. we shall see, and if i mess up, some will learn. thanks for the help i get.  Ed
that, getting Thunderbird icon on task bar, didnt pan out.
also, when i click on the sound icon, or network settings, before i can get the pointer arrow to where i can adjust something, the icon disappears. icons work when i dont hide the taskbar, (stay there), but when i hide the taskbar, suddenly they dont work. hiding the task bar, before i messed up, it didn't matter.
in addition, the icons on the desktop, have moved left, and are squared up. i had spots for those icons before. i cant move some of the ones to trash, that i had moved to trash, before. What i whiner i is..

---

### Post by Dennis N on 2019-01-31
> getting Thunderbird icon on task bar, didnt pan out.

Task bar is for showing/switching open windows.

To put application launchers on the LXDE panel, you need have the "Application Launch Bar" on the panel -  It is there in a default install of Lubuntu 18.04 with a couple of launcher icons already there. You add additional launchers by:

Open Panel Settings > Panel Applets Tab > Select Application Launch Bar > Preferences Button > (Opens Application Launch Bar dialog) > Select the Application from "Installed Applications" > Click the "Add" button. Screenshot of "Application Launch Bar" dialog attached. Shows adding the generic mail reader launcher. (It was empty of launchers before this since I don't use it. I have Plank installed to launch applications)

You can change the order of the launchers with the up and down buttons in the Application Launch Bar window.

---

### Post by oneleded on 2019-02-01
i may have to install plank. the "add' button, "remove" buttonare shaded, and dont work.. when i uninstall / re-install (Application Launch Bar) sometimes the "remove" button is not shaded, most times both are shaded.

---

### Post by Dennis N on 2019-02-01
> **oneleded said:**
> i may have to install plank. the "add' button, "remove" buttonare shaded, and dont work.. when i uninstall / re-install (Application Launch Bar) sometimes the "remove" button is not shaded, most times both are shaded.

All I can suggest on that is that you must select the application first. When you select the application with a mouse click, the 'Add' button is supposed to become active (not grayed). Plank is a good launcher and application switcher for Lubuntu. If you install it, you also have to add 'Plank' to the startup applications or it won't automatically show up. I have my Plank on the left side of the screen and set to autohide, but it can go on any screen edge.

---

### Post by oneleded on 2019-02-01
thanks for trying, i appreciate it.. it seems im stuck on a catch22. i cant use plank, without the add button, i cant work the add button without plank. i get a internal error message ever so often, and send it. next time it shows up i will try an capture the details.

---

### Post by again? on 2019-02-01
Create a new user account and attempt to customize there.
May have better luck with fresh configs.

---

### Post by oneleded on 2019-02-06
i did create a new user account. it was the superuser account. the taskbar was fine there, but as far as being set up, not so much.. however, the add/remove panel items were like the original. i found, i, have to set up the panel items, in a certain order. when i delete an item, it messages up my taskbar. adding the item back doesnt change anything, the taskbar stays messed up. i have 3 spacers on the task bar, an when not in order, its just messed up
another thing that happened; when i click on the icon,, with Application Launch and Taskbar, they started working. i had tried clicking the name before, without results, and the small button that opens and closes option's. it started working. i couldnt have found out these things, without help here. there is a "ghost in the machine", with my lubuntu, perhaps from updating to newer LTS versions, instead if installing Newer LTS versions. soon as i collect my firefox bookmarks. i will reinstall with the iso 18.04 LTS and start over.
on the side;; aint this a blast, trying to figure out how things work.
i installed plank, and docky. both work. i am so close, to installing the panel add/remove panel items, order, of installation, i cant mark as solved as yet.
plank, an docky, are good choices. require less aggravation, thanks, //ed

---

### Post by oneleded on 2019-02-10
i havent marked this solved as yet. when i ; Open Panel Settings> Advanced>Check Automatic hiding.;;  I click the connections icon. the connections window appears. i move the mouse point to what i want to check, of uncheck. before i get close, the window disappears.. for example; Enable Networking, Disconnect. Connection information..  The only way i can get to these is to uncheck Automatic hiding. i didnt have to do this before i messed up the toolbar. there was something before, that let the window stay open. i need to find out. it still has to do with this thread, i dont think i should start another thread at this point.  ed
i have also noticed that firefox is not responding to interaction, with the taskbar. when i click the minus sign, top right corner, next to resize, firefox closes. it does the same if i click on the applet on the toolbar at the bottom. all of this is related somehow.
A correction on firefox; when i cleared the taskbar applets, then applied them in a different order, firefox works correct.

---

### Post by oneleded on 2019-02-12
my toolbar is working for me enough to say solved. the minor issues, is something that needs another thread or so. way later on.

---

### Post by oneleded on 2019-02-14
i should post a new thread; when i messed up the toolbar, automatic hiding will not leave a window open long enough, to click on it, or check mark an item. im just not sure how to phrase it, so it can be understood. when i point to the applet/icon, it doesnt show a window that even says what it is. i know what it is, an has to do with connecting, to the satellite internet. just something is weird. it is a connections icon., to the internet, via satellite. any other applet, when i point to it, a small black window shows up with a description, this applet will not show what it is, though i know how it works.
should i start a new post? is my question. i have had much help on this toolbar thing i messed up on. i want to stay with the right question's. //ed

---

