---
title: "Setting a new FM (File Manager) to default, what about trash?"
date: 2014-12-11
forum: General Help
---

### Post by I.Bun.Tu on 2014-12-11
So whenever I see a guide to switch the default FM in Ubuntu it covers two basic actions. #1 is changing the new FM to default using the .deskop file and #2 is setting the new FM to handle the desktop via gsettings show-icons.

For example, to switch from Nautilus to Nemo (assuming you already have Nemo installed) would be as simple as running the following 3 codes

```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

to switch nemo to default FM, and

```
gsettings set org.gnome.desktop.background show-desktop-icons false

gsettings set org.nemo.desktop show-desktop-icons true
```

to change which FM is responsible for desktop icons.

Now here is the thing I am wondering about. Whenever I have done this, if I want to empty my trash via the launcher icon, I always have to right-click and select empty trash twice in a row to get the empty-trash dialogue to come up. I am wondering if there is some other code that could/needs to be run in order to change which FM is handling the trash bin? Am I correct in even interpretting what is going on here? I am assuming nautilus is still handling the empty trash function in the launcher by default and that's why I need select it twice to get nemo to do it, but I don't really know. Anyone have any ideas?

I am using Ubuntu 14.10 but have noticed this since Ubuntu 13.10; probably earlier, 13.10 is just the first time I remember changing the default FM

---

### Post by CantankRus on 2014-12-12
I came across this as well.
The only solution I found is while nemo is set as default file manager still allow nautilus to draw the desktop which means nautilus 
is still running in the background or don't use the right click quicklist option, just left click.

Right clicking on the rubbish bin and selecting "empty" appears to need nautilus running.
If not running, the first time using the quicklist option will start nautilus.

---

### Post by I.Bun.Tu on 2014-12-13
That is certainly helpful information. If I can find the time, I think I will start looking into what file is being used by the trash icon in the unity launcher and see if there is something in its configuration that points to nautilus.desktop or gnome.desktop and change that to nemo.desktop

If anyone knows about this or which file to look for, please respond. Thanks.

---

### Post by deckoff on 2015-12-08
Ok, anyone had any success with this, i am moving in th same line with no luck...

---

