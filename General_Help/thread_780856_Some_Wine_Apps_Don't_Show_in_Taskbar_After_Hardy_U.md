---
title: "Some Wine Apps Don't Show in Taskbar After Hardy Upgrade? Can this be fixed??"
date: 2008-05-03
forum: General Help
---

### Post by OzzyFrank on 2008-05-03
Among other things this damned upgrade to Hardy Horror did to my system is a peculiar absence of one of my Windows/Wine apps from the taskbar/tasklist when it is open. I tested with a couple of other Wine apps, and they appear on the taskbar, and in Window Selector, but Mailwasher Pro (my most used Windows app by far) doesn't. So if I minimise it, it is basically gone, as you can't restore it from the taskbar, or any docks like AWN, or the Window Selector button, or even key shortcuts like Alt+Esc or Alt+Tab. It is in effect gone, though it is still open and doing its thing.

So does anyone know a fix or workaround? Or even a way of restoring the app while open (like other keyboard shortcuts or anything)? Cheers

---

### Post by Rocket2DMn on 2008-05-03
Have you disabled the Gutsy repos for wine and added the Hardy ones?  Go to System->Administration->Software Sources, hit the Third Party Software tab and uncheck wine for Gutsy Gibbon.  Close this dialog, let it update, then add repos for Hardy as shown here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) (there are 2 lines that you have to run from here)
Then run
```
sudo apt-get update
sudo apt-get upgrade
```
Hopefully that should help.

---

### Post by OzzyFrank on 2008-05-03
Hi. I haven't actually had the Wine repo in my sources since Edgy or maybe Feisty... just installed it via Synaptic and let it update with Update Manager (Gutsy was a clean install). Reading that Wine page I see I actually should be updating Wine manually with each distro upgrade.

The link they gave to the deb was invalid, but at least they give instructions how to reinstall Wine (didn't think one would actually have to reinstall it though). Except... I go to **Applications->Add/Remove** and search for Wine but it apparently doesn't exist! And using **sudo apt-get update** looked like it was going to work but seems it didn't (ended in errors). In **Synaptic** Wine was already installed but I could _right-click it_ and choose **Mark for Upgrade** and it seems to have downloaded and installed fine.

And Mailwasher Pro now is in the task list! (Except now there's also a button for **Wine System Tray** there, so will have to look into how to hide that? Oh, OK, if you get that just click the link for the app like Mailwasher inside and the Wine System Tray will disappear).

So thanks to Rocket2DMn for the info and link, and hope this edited version of the official help on that page helps someone else (who needs to do this and finds the official guide to not work). Cheers (PS: I would have thought by now that Wine would be upgraded along with Ubuntu, since so many people have it, but I suppose that is just wishful thinking, and no matter how much you see Wine as being "part of the system", it really is just another app after all. But still...).

---

### Post by Rocket2DMn on 2008-05-03
So it's working then?  Link me to the wiki that you were reading from, and I might be able to fix it for others.
Did you just have to add the repo, update, upgrade and you were good to go?

---

### Post by OzzyFrank on 2008-05-03
Hiya. I just used the link you provided [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and worked around what didn't work for me there. So my steps were the first 3 from that page, being (in terminal):

**wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -**

then:

**sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list**

then:

**sudo apt-get update**

Since **sudo apt-get upgrade** didn't work for me, I opened **Synaptic** and searched for Wine, right-clicked it and chose **Mark for Upgrade**. Now it all seems to work fine (Wine seemed to be working quite fine before doing all this, except for the taskbar thingy of course, but now it seems 100%).

---

### Post by OzzyFrank on 2008-05-04
No big deal, but thought I would mention I am still getting that Wine System Tray appearing as a small box/window and as a taskbar button. I found I don't need to click Mailwasher's icon from within that box, just click the one on the taskbar and the Wine System Tray button disappears from the taskbar. I still haven't rebooted yet, so that may fix it. Like I said, barely worth mentioning, but is a fact that is related and shouldn't be left out.

---

### Post by OzzyFrank on 2008-05-05
Err... now Mailwasher Pro won't show at all... had this problem after building my new PC and going to 64-bit Gutsy. Only solution was upgrading the app from 3.2 to 6.1, but that version is already on my system, and I just even tried a reinstall of it to no avail. Even tried a reinstall through Synaptic (of Wine that is). It loads but doesn't show at all... and I never played with Wine, was just trying to fix Compiz and a few reboots later no Mailwasher (tried a few other Wine apps and all seemed well). Any ideas anyone? Or time for a new thread?

---

### Post by Rocket2DMn on 2008-05-05
64 bit has a number of issues, and wine is one of them.  I'm still trying to troubleshoot some issues myself, but you may consider reinstalling with the 32 bit version of Ubuntu, I think I might take that path if I can't nail down my own problems.

---

### Post by OzzyFrank on 2008-05-05
I might try and and stick with 64-bit Wine for now, but in case I bite the bullet, how would I go about installing the 32-bit version? Taking into account Ubuntu will complain that it is for the wrong architecture. Will the **--force** option in a terminal suffice?

---

### Post by Rocket2DMn on 2008-05-06
By 32 bit version I mean you need to reinstall Ubuntu using the i386 version, not the amd64 version.

---

