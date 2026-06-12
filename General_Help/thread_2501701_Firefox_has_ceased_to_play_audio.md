---
title: "Firefox has ceased to play audio"
date: 2024-10-17
forum: General Help
---

### Post by johngw on 2024-10-17
I'm running Kubuntu 24.04 and Firefox has ceased to play any audio. I can get audio on other programs, so my first suspicion was a Firefox problem. However, Google searches have revealed nothing relating to Firefox sound only. But they have revealed a problem from a couple of years back when Firefox dropped support for Alsa. Could this be the problem.

One of my search results suggested running
```
[FONT=monospace][COLOR=#000000] [/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]snap connections firefox[/COLOR][/FONT][FONT=monospace]    
[/FONT]
```
which I did, despite the fact I thought I'd uninstalled the snap version of Firefox and installed the Debian version. And lo and behold I got a result, which informed me, amongst other lines
```
[FONT=monospace][COLOR=#000000]Interface               Plug                             Slot                            Notes [/COLOR]
alsa                    firefox:alsa                     -                               -

[/FONT]
```

Could this be my problem? And is the problem with the snap version of Firefox? If so, how can I get myself back to the Debian version?

Or am I barking up the wrong tree entirely?

All suggestions gratefully received.

---

### Post by 1fallen on 2024-10-17
Start at Step 2: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
If it works then you can remove that snap version

---

### Post by johngw on 2024-10-17
> **1fallen2 said:**
> Start at Step 2: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
If it works then you can remove that snap version

Thanks. That gets me back to the version I want to have, but still no audio. And how do I stop the Snap version coming back?

---

### Post by 1fallen on 2024-10-17
> **johngw said:**
> Thanks. That gets me back to the version I want to have, but still no audio. And how do I stop the Snap version coming back?
If you followed all on that page it takes care of that with the higher priority.

Audio and firefox has no issues here.

---

### Post by johngw on 2024-10-17
> **1fallen2 said:**
> If you followed all on that page it takes care of that with the higher priority.

Audio and firefox has no issues here.

But the Snap version sneaked back even after I'd done that. But I'll keep monitoring the situation. thanks for the help.

And I'll keep looking for a solution to the audio problem.

---

### Post by 1fallen on 2024-10-17
How many snaps are you using now?
```
snap list
```

---

### Post by johngw on 2024-10-17
> **johngw said:**
> But the Snap version sneaked back even after I'd done that. But I'll keep monitoring the situation. thanks for the help.

And I'll keep looking for a solution to the audio problem.

And suddenly I've got sound again. It must have been the Snap version that was the problem. Though I'm not sure why uninstalling it didn't cure the problem immediately.

---

### Post by johngw on 2024-10-17
> **1fallen2 said:**
> How many snaps are you using now?
```
snap list
```

```
[FONT=monospace][COLOR=#000000]Name                    Version                   Rev    Tracking         Publisher      Notes [/COLOR]
bare                    1.0                       5      latest/stable    canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     base [/COLOR]
core20                  20240705                  2379   latest/stable    canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     base [/COLOR]
core22                  20240904                  1621   latest/stable    canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     base [/COLOR]
curl                    8.1.2                     1754   latest/stable    woutervb       - 
fbreader                2.1.2                     30     latest/stable    fbreader       - 
foliate                 3.1.1                     1818   latest/stable    johnfactotum   - 
gedit                   46.1                      684    latest/stable    canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     - [/COLOR]
gnome-3-38-2004         0+git.efb213a             143    latest/stable/…  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     - [/COLOR]
gnome-42-2204           0+git.510a601             176    latest/stable    canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     - [/COLOR]
gtk-common-themes       0.1-81-g442e511           1535   latest/stable/…  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     - [/COLOR]
snapd                   2.63                      21759  latest/stable    canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     snapd [/COLOR]
thunderbird             128.3.1esr-1              532    latest/stable    canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]     - [/COLOR]
webkitgtk-6-gnome-2204  0+git.3c2f6a6             31     latest/stable    snapcrafters[COLOR=#ffff54]&#10026;[/COLOR][COLOR=#000000]  - [/COLOR]
yt-dlp                  2024.08.06-21-gd1c4d88b2  689    latest/stable    degville       -

[/FONT]
```

---

### Post by 1fallen on 2024-10-17
My next question is.........(drum roll) do you want to keep them?

My first command after a clean Install:
```
sudo apt autoremove --purge snapd
```
Then no more sneaks with:
```
sudo apt-mark hold snapd
```

That is a choice you would have to decide for yourself though.

EDIT: Nice that sound is working though.

---

### Post by johngw on 2024-10-17
I'm not sure if I want to keep them or not. I don't use Thunderbird and do I need the gnome modules seeing as I use Kubuntu? The rest i don't recognise. are any essential?

---

### Post by johngw on 2024-10-18
> **1fallen2 said:**
> My next question is.........(drum roll) do you want to keep them?

My first command after a clean Install:
```
sudo apt autoremove --purge snapd
```
Then no more sneaks with:
```
sudo apt-mark hold snapd
```

That is a choice you would have to decide for yourself though.

EDIT: Nice that sound is working though.

I'll risk getting rid of them. I can't think why I would want to keep them. And I suppose it's pretty straightforward to reinstall anything I need. So here goes!

---

### Post by 1fallen on 2024-10-18
Yep anything needing a reinstall will be the old usual apt install.

I'm going out on limb but I think you'll be happier without them. ;)

---

### Post by johngw on 2024-10-18
> **1fallen2 said:**
> Yep anything needing a reinstall will be the old usual apt install.

I'm going out on limb but I think you'll be happier without them. ;)

That's what I suspected. So I no longer have them. :o

---

