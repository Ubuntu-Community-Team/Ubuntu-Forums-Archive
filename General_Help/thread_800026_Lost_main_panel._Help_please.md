---
title: "Lost main panel. Help please"
date: 2008-05-19
forum: General Help
---

### Post by Mirza on 2008-05-19
Hi all,

After installing compiz-fusion my ubuntu system seemed to work fine. But after launchin few programs my main pane (where syte, administration, clock is) disappeared.I restarted it in failsafe tryed reconfiguring X but with no help. I cant launch applications with alt+f2 only. When sytem starts i see the panel for 5-6 secs then it disappeares. 

Thanks for help in advance

---

### Post by Het Irv on 2008-05-19
What version of Compiz were you trying to install, and how?
Do you still see the bottom panel?

---

### Post by phidia on 2008-05-19
Is gnome desktop crashing on you? You can usually get another panel by right clicking the desktop and choosing create new panel-I'm not sure of the exact menu item but the menu for that should appear with a right click.
If you are getting error messages please include those.

---

### Post by Mirza on 2008-05-19
No bottom i always delete. I installed last one version. And system is updated. Problem is i restarted it few times and it worked just fine. Then i was tryin to make playlist for amarok when it happened. Now when I enter system i can play with compiz efects but i only have wallpaper without icons, nothing else...


When i right click i dont get anything. No error and it doesnt crash i just lost panel

---

### Post by issih on 2008-05-19
Couple of things you could try.

The actual application name of the panels seems to be "gnome-panel", so you could do alt F2 then type "gnome-terminal" to get a terminal window up.

From the terminal type "ps -eaf | grep gnome-panel" to see if there are processes that should draw panels actually running. If there are not launch one with the command "gnome-panel" and hope that whatever happened was a bizarre glitch.

Finally running "metacity --replace" ought to shut compiz off, and return you to the default gnome window manager, so you can see if the panels are running somewhere, but being hidden by compiz behaving oddly, or if the panel is in fact crashing.

Let us know how it goes

---

### Post by Het Irv on 2008-05-19
Can you reinstall gnome?
```
sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop
```

**Last resort**

---

### Post by Mirza on 2008-05-19
issih metacity --replace helped. After shuting down compiz-fusion my panel was back. Now I have ati graphic card. Will using restricted drivers help with compiy cause it seems I have problems with thesee

---

### Post by issih on 2008-05-19
Sadly I've never tried to use compiz with an ati card (as it happens I will have one arriving by post in the next few days, but thats not useful now). As a general rule nvidia cards are easier to get working smoothly, but it should be possible to get an ati card to play nicely.

It is definitely worth giving the restricted drivers a whirl as a first step. Just enabling the ones offered by default may sort you out, but if not it would probably be worth getting hold of envy which is a management utility written by Alberto Milone (who pops up in these forums from time to time). Have a read here:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

In essence it automates the process of getting hold of the very latest graphics drivers and installing them properly under ubuntu, its worked fine for me with nvidia cards, so fingers crossed its magic works as well for ati.

Assuming you are running hardy heron (ubuntu 8.04) you want the latest version envyng, which handily is in the repositories, so can be installed via the synaptic package manager.

If you aren't sure about how to go about that, just ask...

Hope thats useful

---

