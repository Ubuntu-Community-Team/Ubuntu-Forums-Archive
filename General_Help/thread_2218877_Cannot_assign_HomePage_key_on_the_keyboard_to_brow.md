---
title: "Cannot assign HomePage key on the keyboard to browser in Ubuntu 14.04"
date: 2014-04-22
forum: General Help
---

### Post by dr-ashishyadav on 2014-04-22
Earlier, I was using Ubuntu 13.04 in which the HomePage key of my laptop keyboard was auto assigned to launch the browser. After performing a clean install of 14.04, this key is now auto assigned to open my Home folder. I have tried assigning it in System Settings > Keyboard > Shortcuts > Launchers to 'Launch web browser' while simultaneously disabling the 'Home folder' launcher but to no avail. The HomePage key is still assigned to launching the Home folder even after reboot. Disabling both the both the above mentioned launchers is also without effect  and even after reboot the HomePage key still remains assigned to the Home folder. :confused: Help please.

---

### Post by Jordan_Cameron on 2014-04-22
Out of interest are you able to reassign other keys?  For instance, the XF86AudioRaiseVolume key (raise volume), are you able to say, reassign it to lower the volume instead?  It sounds like it may be a bug in 14.04, but I can't be too sure.

---

### Post by Mr._Pipiens on 2014-04-23
I have the same problem; any use of the HomePage key including combos (CTRL-HomePage, Alt-HomePage, etc.) launches the Home folder. I'm trying to get used to using Super-3 (Firefox is the 3[SUP]rd[/SUP] item in my Unity launcher). In the meantime, I have my fingers crossed for an appropriate update.

---

### Post by ahendriks on 2014-05-29
I am having the same problem as you do. The homepage key opens the filemanager (nemo in my case/nautilus for a clean install).
Does anybody have a sollution for this problem?

---

### Post by zteam2 on 2014-05-29
I have a similair issue, I always assign CTRL + ESCAPE to xkill, but this no longer works in 14.04

---

### Post by shgysk8zer0 on 2015-01-02
After fighting with my media keys for quite some time, I finally got most of them assigned correctly using ```
gsettings reset org.gnome.settings-daemon.plugins.media-keys $key
```
Despite having set "HomePage" on "Lauch web browser", it does not open my default browser when pressed. It does, however, return me to home in certain applications (/home/$user in nautilus, about:home in Firefox).
```

$ gsettings list-recursively  org.gnome.settings-daemon.plugins.media-keys
org.gnome.settings-daemon.plugins.media-keys logout '<Control><Alt>Delete'
org.gnome.settings-daemon.plugins.media-keys screenreader ''
org.gnome.settings-daemon.plugins.media-keys volume-mute 'XF86AudioMute'
org.gnome.settings-daemon.plugins.media-keys volume-up 'XF86AudioRaiseVolume'
org.gnome.settings-daemon.plugins.media-keys window-screenshot '<Alt>Print'
org.gnome.settings-daemon.plugins.media-keys previous 'XF86AudioPrev'
org.gnome.settings-daemon.plugins.media-keys stop 'XF86AudioStop'
org.gnome.settings-daemon.plugins.media-keys home 'XF86Explorer'
org.gnome.settings-daemon.plugins.media-keys terminal '<Control><Alt>t'
org.gnome.settings-daemon.plugins.media-keys screenshot-clip '<Ctrl>Print'
org.gnome.settings-daemon.plugins.media-keys magnifier ''
org.gnome.settings-daemon.plugins.media-keys help ''
org.gnome.settings-daemon.plugins.media-keys search 'XF86Search'
org.gnome.settings-daemon.plugins.media-keys custom-keybindings @as []
org.gnome.settings-daemon.plugins.media-keys magnifier-zoom-in ''
org.gnome.settings-daemon.plugins.media-keys calculator 'XF86Calculator'
org.gnome.settings-daemon.plugins.media-keys eject 'XF86Eject'
org.gnome.settings-daemon.plugins.media-keys window-screenshot-clip '<Ctrl><Alt>Print'
org.gnome.settings-daemon.plugins.media-keys area-screenshot-clip '<Ctrl><Shift>Print'
org.gnome.settings-daemon.plugins.media-keys media 'XF86AudioMedia'
org.gnome.settings-daemon.plugins.media-keys www 'HomePage'
org.gnome.settings-daemon.plugins.media-keys play 'XF86AudioPlay'
org.gnome.settings-daemon.plugins.media-keys email 'XF86Mail'
org.gnome.settings-daemon.plugins.media-keys volume-down 'XF86AudioLowerVolume'
org.gnome.settings-daemon.plugins.media-keys decrease-text-size ''
org.gnome.settings-daemon.plugins.media-keys on-screen-keyboard ''
org.gnome.settings-daemon.plugins.media-keys next 'XF86AudioNext'
org.gnome.settings-daemon.plugins.media-keys screenshot 'Print'
org.gnome.settings-daemon.plugins.media-keys increase-text-size ''
org.gnome.settings-daemon.plugins.media-keys magnifier-zoom-out ''
org.gnome.settings-daemon.plugins.media-keys priority 0
org.gnome.settings-daemon.plugins.media-keys screencast '<Ctrl><Shift><Alt>R'
org.gnome.settings-daemon.plugins.media-keys screensaver '<Control><Alt>l'
org.gnome.settings-daemon.plugins.media-keys toggle-contrast ''
org.gnome.settings-daemon.plugins.media-keys pause ''
org.gnome.settings-daemon.plugins.media-keys active true
org.gnome.settings-daemon.plugins.media-keys area-screenshot '<Shift>Print'

```

As you can see, media keys are assigned using 'XF86*', so I tried
```
gsettings set org.gnome.settings-daemon.plugins.media-keys www 'XF86HomePage'
```
and it worked. Unlike 'Mail', however, pressing this button when my default browser is already open,
it opens a new window instead of raising it. I have not yet actually opened since I only fixed this issue
while writing this comment, but I am fairly certain it will work.

**Edit:**It does, in fact, open my default browser.

---

### Post by ahendriks on 2015-01-03
Thx, this does work perfectly!

---

