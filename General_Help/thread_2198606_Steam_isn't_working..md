---
title: "Steam isn't working."
date: 2014-01-09
forum: General Help
---

### Post by ilikecolors on 2014-01-09
Yesterday, I was ready to turn off my laptop and suddenly Steam started updating. I had to go, so I clicked "Cancel" and it stopped updating like it always does. Today, I tried playing Portal and it would'nt open. I tried opening Steam and that wouldn't work, either. Finally, I uninstalled it via the Software Center and installed it once more. I tried opening Portal, and then Steam. It wouldn't work. I restarted my coputer and tried again. Still wouldn't work. Pleas help, I have a lot of games on Steam and I really don't want to lose them or my saves. Im running on 13.10. Please help!

---

### Post by kostkon on 2014-01-10
> **ilikecolors said:**
> Yesterday, I was ready to turn off my laptop and suddenly Steam started updating. I had to go, so I clicked "Cancel" and it stopped updating like it always does. Today, I tried playing Portal and it would'nt open. I tried opening Steam and that wouldn't work, either. Finally, I uninstalled it via the Software Center and installed it once more. I tried opening Portal, and then Steam. It wouldn't work. I restarted my coputer and tried again. Still wouldn't work. Pleas help, I have a lot of games on Steam and I really don't want to lose them or my saves. Im running on 13.10. Please help!
Try running it from the terminal and see if you'll get any error messages. Obviously, you don't need to worry about your saves since they are saved in the cloud.

---

### Post by jones quest on 2014-01-10
You can uninstall steam and remove everything in your steam folder .local/share/Steam except for the SteamApps folder (which contains you installed games) and the clientregistry.blob (which contains the index of the installed games). Then reinstall steam. 

As pointed out before your save-games are on the steam server.

---

### Post by ilikecolors on 2014-01-10
> **jones quest said:**
> You can uninstall steam and remove everything in your steam folder .local/share/Steam except for the SteamApps folder (which contains you installed games) and the clientregistry.blob (which contains the index of the installed games). Then reinstall steam. 

As pointed out before your save-games are on the steam server.

Theres no such thing as clientregistry.blob :confused:

---

### Post by efflandt on 2014-01-10
There should be a **ClientRegistry.blob** (capitalization is important in Linux), or at least mine has that in ~/.local/share/Steam/

During some update last summer Linux steam stopped working properly and the fix was to rm something. Now that I think about it **appcache** sounds very familiar. So that fix might have been: rm -r ~/.local/share/steam/appcache

But since I am not absolutely certain that would be a fix, you could instead try temporarily renaming that folder in ~/.local/share/Steam/ to something like **appcache-backup** and see if steam runs or updates itself and runs.

Note that Steam Cloud keeps track of what games you own, so even if you install steam from scratch on a different computer or OS, any of your games suitable for that OS should show up in your Library. The Cloud also keeps track of items and achievements, at least for most multi-player games, but might not for some single player games, especially those under development. For example when my Linux partition failed and I installed steam in Win7 my TF2 items/achievements were there. And likewise when I installed Steam in Win7 on new gaming laptop, and then in Ubuntu 13.10 once I figured out bumblebee (optirun).

---

### Post by ilikecolors on 2014-01-12
> **efflandt said:**
> There should be a **ClientRegistry.blob** (capitalization is important in Linux), or at least mine has that in ~/.local/share/Steam/

During some update last summer Linux steam stopped working properly and the fix was to rm something. Now that I think about it **appcache** sounds very familiar. So that fix might have been: rm -r ~/.local/share/steam/appcache

But since I am not absolutely certain that would be a fix, you could instead try temporarily renaming that folder in ~/.local/share/Steam/ to something like **appcache-backup** and see if steam runs or updates itself and runs.

Note that Steam Cloud keeps track of what games you own, so even if you install steam from scratch on a different computer or OS, any of your games suitable for that OS should show up in your Library. The Cloud also keeps track of items and achievements, at least for most multi-player games, but might not for some single player games, especially those under development. For example when my Linux partition failed and I installed steam in Win7 my TF2 items/achievements were there. And likewise when I installed Steam in Win7 on new gaming laptop, and then in Ubuntu 13.10 once I figured out bumblebee (optirun).

Haha, there isn't even an appcache. And yes, I have hidden files showing. Should I just do it anyway? Do you want a screenshot? Theres not even a file that seems equally important...

---

### Post by ilikecolors on 2014-01-14
Should I simply just delete everything except Steamapps?

---

### Post by jones quest on 2014-01-27
Yes.

If both appcache and ClientRegistry.blob are missing the you may as well delete everything except:
~/.local/share/Steam/SteamApps/ and the files and folders within (so you don't have to re-download the games).
And reinstall steam from scratch.

Most steam games save local game data to ~/.local/share/[game X].

---

