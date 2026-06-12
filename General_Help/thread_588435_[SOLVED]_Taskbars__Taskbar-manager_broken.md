---
title: "[SOLVED] Taskbars / Taskbar-manager broken"
date: 2007-10-23
forum: General Help
---

### Post by perixx on 2007-10-23
At first, I was convinced that I've lost all my personal settings during an update in Xubuntu 7.04's Synaptic (only the symlinks for Thunar, Trashbin and mounted drives are left).

Now I think it's more a problem of the Taskbar/Taskbar-Manager being broken, since I have access to all menu's and programs via rightlick on the desktop. I believe that I also discovered the settings still being in place with the 'volume manager'.

The only problem: the Taskbars are not being displayed at all, among with the menu button. 
So, I assume that the 'pointer' to that Taskbar-settings, which tells Xfce in which locations to look for them, or the Taskbar-module itself has blown up!

Where could I check out this Taskbar-settings-'pointer' and how could the Taskbar-module be restored without destroying the settings?


Additionally, it was good to find out, in which locations Xfce does store personal desktop settings, respectively the profile settings... 
Are there also settings stored outside of /home/USER?
I know of home/USER/.config/xfce4/panel/panels.xml stores some settings data, e.g.

Thanks for your help!


perixx

---

### Post by perixx on 2007-10-24
Are, am I on my own with this...?


By the way, resetting the repositories to the Ubuntu's standard and doing 'sudo apt-get install xubuntu-desktop' didn't fix my problem - it said, the desktop was already installed and up to date.

Would I lose my personal settings and app-specific settings, if I'd remove and re-install the desktop?


perixx

---

### Post by perixx on 2007-10-24
Seems like the problem boils down to the Taskbar-module that's non-funcional...

The taskbars aren't displayed on the desktop and I can't access the Taskbar-manager in the 'Settings-manager'. Also, if I start an application via context-application-menu or the Terminal, it starts smoothly - apart from Firefox, which takes 2 tries the first time - but if I minimize it, the application 'gets lost' in the background, for there's no taskbar to minimize to (I don't know if they could be re-activated with some Terminal task-switching-command, though).

So, it would be very likely helpful, if someone could provide me with some info on how to remove and re-install the taskbar-module without overwriting it's personal settings..!

Help's appreciated ;]


perixx

---

### Post by perixx on 2007-10-25
Nobody has a clue for me ? Do I need to reinstall ?

[-o<

---

### Post by perixx on 2007-10-26
PROBLEM SOLVED !!

[http://ubuntuforums.org/archive/index.php/t-415082.html](http://ubuntuforums.org/archive/index.php/t-415082.html)

Analog to this nifty problem-solver, all I needed to do was
a) opening the Terminal > start 'xfce4-panel'
b) Applications > Settings > Settings Manager > ('Desktop/Workplace') > Tab ('Preferences') > check desired 'Show Icons for...' checkboxes
c) restart via Shutdown-Button

Voilà!


perixx

---

