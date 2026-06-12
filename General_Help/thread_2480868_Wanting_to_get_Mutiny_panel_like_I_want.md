---
title: "Wanting to get Mutiny panel like I want"
date: 2022-11-12
forum: General Help
---

### Post by SciGuy1872 on 2022-11-12
Hi. I'm using Ubuntu Mate 20.04 and want to get the Mutiny panel the way I want it--the launcher icons for Steam and Dosbox games surrounded by a square line and different shading, so as to stand out from the panel. See the attachment for the icons not treated like other launchers.

---

### Post by MAFoElffen on 2022-11-13
If you install 'dconf editor' or you can set by the cli...

The setting you want to play with are located underorg.gnome.shell.extensions.dash-to-dock. The settings you are wanting to change are "force-square-corners true". background color. transparency.

---

### Post by SciGuy1872 on 2022-11-14
Hi.  Thanks for the info and help--I couldn't find the file with the manager; what's the name of the file again and what is the path?  Could my problem be because I don't have Gnome extension installed, given that I have the mate branch and not the stock ubuntu?

Thanks again,
         Anthony

---

### Post by SciGuy1872 on 2022-11-14
Hi.  I ran dconf editor and selected org, then clicked gnome, shell, and finally the category extensions, but under extensions, there is no category named "dash-to-dock".  Wondering what to do?

---

### Post by SciGuy1872 on 2022-11-14
I think I can't install Gnome extensions in Mate, so the dconf edit on org.gnome.shell.extensions.dash-to-dock doesn't apply to me.  Hopefully, there is some way to make the Mutiny panel in Mate look the same throughout the panel.  If someone has an Idea that works with Mate, I would appreciate the help.  I've attached the screenshot of the issue since that was displayed a couple of posts ago.  Thanks.

---

### Post by MAFoElffen on 2022-11-15
In dconf editor... or via cli
```

mafoelffen@Mikes-ThinkPad-T520:~$ gsettings list-recursively 
org.gnome.shell.extensions.dash-to-dock
org.gnome.shell.extensions.dash-to-dock activate-single-window true
org.gnome.shell.extensions.dash-to-dock animate-show-apps true
org.gnome.shell.extensions.dash-to-dock animation-time 0.20000000000000001
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-1 ['<Ctrl><Super>1']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-10 ['<Ctrl><Super>0']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-2 ['<Ctrl><Super>2']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-3 ['<Ctrl><Super>3']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-4 ['<Ctrl><Super>4']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-5 ['<Ctrl><Super>5']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-6 ['<Ctrl><Super>6']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-7 ['<Ctrl><Super>7']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-8 ['<Ctrl><Super>8']
org.gnome.shell.extensions.dash-to-dock app-ctrl-hotkey-9 ['<Ctrl><Super>9']
org.gnome.shell.extensions.dash-to-dock app-hotkey-1 ['<Super>1']
org.gnome.shell.extensions.dash-to-dock app-hotkey-10 ['<Super>0']
org.gnome.shell.extensions.dash-to-dock app-hotkey-2 ['<Super>2']
org.gnome.shell.extensions.dash-to-dock app-hotkey-3 ['<Super>3']
org.gnome.shell.extensions.dash-to-dock app-hotkey-4 ['<Super>4']
org.gnome.shell.extensions.dash-to-dock app-hotkey-5 ['<Super>5']
org.gnome.shell.extensions.dash-to-dock app-hotkey-6 ['<Super>6']
org.gnome.shell.extensions.dash-to-dock app-hotkey-7 ['<Super>7']
org.gnome.shell.extensions.dash-to-dock app-hotkey-8 ['<Super>8']
org.gnome.shell.extensions.dash-to-dock app-hotkey-9 ['<Super>9']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-1 ['<Shift><Super>1']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-10 ['<Shift><Super>0']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-2 ['<Shift><Super>2']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-3 ['<Shift><Super>3']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-4 ['<Shift><Super>4']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-5 ['<Shift><Super>5']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-6 ['<Shift><Super>6']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-7 ['<Shift><Super>7']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-8 ['<Shift><Super>8']
org.gnome.shell.extensions.dash-to-dock app-shift-hotkey-9 ['<Shift><Super>9']
org.gnome.shell.extensions.dash-to-dock apply-custom-theme false
org.gnome.shell.extensions.dash-to-dock apply-glossy-effect true
org.gnome.shell.extensions.dash-to-dock autohide true
org.gnome.shell.extensions.dash-to-dock autohide-in-fullscreen false
[COLOR=#ff0000]org.gnome.shell.extensions.dash-to-dock background-color '#ffffff'
org.gnome.shell.extensions.dash-to-dock background-opacity 0.80000000000000004[/COLOR]
org.gnome.shell.extensions.dash-to-dock bolt-support true
org.gnome.shell.extensions.dash-to-dock click-action 'cycle-windows'
org.gnome.shell.extensions.dash-to-dock custom-background-color false
org.gnome.shell.extensions.dash-to-dock custom-theme-customize-running-dots false
org.gnome.shell.extensions.dash-to-dock custom-theme-running-dots-border-color '#ffffff'
org.gnome.shell.extensions.dash-to-dock custom-theme-running-dots-border-width 0
org.gnome.shell.extensions.dash-to-dock custom-theme-running-dots-color '#ffffff'
org.gnome.shell.extensions.dash-to-dock custom-theme-shrink false
org.gnome.shell.extensions.dash-to-dock customize-alphas false
org.gnome.shell.extensions.dash-to-dock dash-max-icon-size 48
org.gnome.shell.extensions.dash-to-dock disable-overview-on-startup false
org.gnome.shell.extensions.dash-to-dock dock-fixed false
org.gnome.shell.extensions.dash-to-dock dock-position 'BOTTOM'
org.gnome.shell.extensions.dash-to-dock extend-height false
[COLOR=#ff0000]org.gnome.shell.extensions.dash-to-dock force-straight-corner false[/COLOR]
org.gnome.shell.extensions.dash-to-dock height-fraction 0.90000000000000002
org.gnome.shell.extensions.dash-to-dock hide-delay 0.20000000000000001
org.gnome.shell.extensions.dash-to-dock hot-keys true
org.gnome.shell.extensions.dash-to-dock hotkeys-overlay true
org.gnome.shell.extensions.dash-to-dock hotkeys-show-dock true
org.gnome.shell.extensions.dash-to-dock icon-size-fixed false
org.gnome.shell.extensions.dash-to-dock intellihide true
org.gnome.shell.extensions.dash-to-dock intellihide-mode 'FOCUS_APPLICATION_WINDOWS'
org.gnome.shell.extensions.dash-to-dock isolate-locations true
org.gnome.shell.extensions.dash-to-dock isolate-monitors false
org.gnome.shell.extensions.dash-to-dock isolate-workspaces false
org.gnome.shell.extensions.dash-to-dock max-alpha 0.80000000000000004
org.gnome.shell.extensions.dash-to-dock middle-click-action 'launch'
org.gnome.shell.extensions.dash-to-dock min-alpha 0.20000000000000001
org.gnome.shell.extensions.dash-to-dock minimize-shift true
org.gnome.shell.extensions.dash-to-dock multi-monitor false
org.gnome.shell.extensions.dash-to-dock preferred-monitor -2
org.gnome.shell.extensions.dash-to-dock preferred-monitor-by-connector 'primary'
org.gnome.shell.extensions.dash-to-dock pressure-threshold 100.0
org.gnome.shell.extensions.dash-to-dock preview-size-scale 0.0
org.gnome.shell.extensions.dash-to-dock require-pressure-to-show true
org.gnome.shell.extensions.dash-to-dock running-indicator-dominant-color false
org.gnome.shell.extensions.dash-to-dock running-indicator-style 'DEFAULT'
org.gnome.shell.extensions.dash-to-dock scroll-action 'do-nothing'
org.gnome.shell.extensions.dash-to-dock scroll-switch-workspace true
org.gnome.shell.extensions.dash-to-dock scroll-to-focused-application true
org.gnome.shell.extensions.dash-to-dock shift-click-action 'minimize'
org.gnome.shell.extensions.dash-to-dock shift-middle-click-action 'launch'
org.gnome.shell.extensions.dash-to-dock shortcut ['<Super>q']
org.gnome.shell.extensions.dash-to-dock shortcut-text '<Super>q'
org.gnome.shell.extensions.dash-to-dock shortcut-timeout 2.0
org.gnome.shell.extensions.dash-to-dock show-apps-at-top false
org.gnome.shell.extensions.dash-to-dock show-delay 0.25
org.gnome.shell.extensions.dash-to-dock show-favorites true
org.gnome.shell.extensions.dash-to-dock show-mounts true
org.gnome.shell.extensions.dash-to-dock show-mounts-network false
org.gnome.shell.extensions.dash-to-dock show-mounts-only-mounted true
org.gnome.shell.extensions.dash-to-dock show-running true
org.gnome.shell.extensions.dash-to-dock show-show-apps-button true
org.gnome.shell.extensions.dash-to-dock show-trash true
org.gnome.shell.extensions.dash-to-dock show-windows-preview true
[COLOR=#ff0000]org.gnome.shell.extensions.dash-to-dock transparency-mode 'DEFAULT'[/COLOR]
org.gnome.shell.extensions.dash-to-dock unity-backlit-items false
org.gnome.shell.extensions.dash-to-dock workspace-agnostic-urgent-windows true
000000000001
org.gnome.shell.extensions.dash-to-dock hot-keys true
org.gnome.shell.extensions.dash-to-dock hotkeys-overlay true
org.gnome.shell.extensions.dash-to-dock hotkeys-show-dock true
org.gnome.shell.extensions.dash-to-dock icon-size-fixed false
org.gnome.shell.extensions.dash-to-dock intellihide true
org.gnome.shell.extensions.dash-to-dock intellihide-mode 'FOCUS_APPLICATION_WINDOWS'
org.gnome.shell.extensions.dash-to-dock isolate-locations true
org.gnome.shell.extensions.dash-to-dock isolate-monitors false
org.gnome.shell.extensions.dash-to-dock isolate-workspaces false
org.gnome.shell.extensions.dash-to-dock max-alpha 0.80000000000000004
org.gnome.shell.extensions.dash-to-dock middle-click-action 'launch'
org.gnome.shell.extensions.dash-to-dock min-alpha 0.20000000000000001
org.gnome.shell.extensions.dash-to-dock minimize-shift true
org.gnome.shell.extensions.dash-to-dock multi-monitor false
org.gnome.shell.extensions.dash-to-dock preferred-monitor -2
org.gnome.shell.extensions.dash-to-dock preferred-monitor-by-connector 'primary'
org.gnome.shell.extensions.dash-to-dock pressure-threshold 100.0
org.gnome.shell.extensions.dash-to-dock preview-size-scale 0.0
org.gnome.shell.extensions.dash-to-dock require-pressure-to-show true
org.gnome.shell.extensions.dash-to-dock running-indicator-dominant-color false
org.gnome.shell.extensions.dash-to-dock running-indicator-style 'DEFAULT'
org.gnome.shell.extensions.dash-to-dock scroll-action 'do-nothing'
org.gnome.shell.extensions.dash-to-dock scroll-switch-workspace true
org.gnome.shell.extensions.dash-to-dock scroll-to-focused-application true
org.gnome.shell.extensions.dash-to-dock shift-click-action 'minimize'
org.gnome.shell.extensions.dash-to-dock shift-middle-click-action 'launch'
org.gnome.shell.extensions.dash-to-dock shortcut ['<Super>q']
org.gnome.shell.extensions.dash-to-dock shortcut-text '<Super>q'
org.gnome.shell.extensions.dash-to-dock shortcut-timeout 2.0
org.gnome.shell.extensions.dash-to-dock show-apps-at-top false
org.gnome.shell.extensions.dash-to-dock show-delay 0.25
org.gnome.shell.extensions.dash-to-dock show-favorites true
org.gnome.shell.extensions.dash-to-dock show-mounts true
org.gnome.shell.extensions.dash-to-dock show-mounts-network false
org.gnome.shell.extensions.dash-to-dock show-mounts-only-mounted true
org.gnome.shell.extensions.dash-to-dock show-running true
org.gnome.shell.extensions.dash-to-dock show-show-apps-button true
org.gnome.shell.extensions.dash-to-dock show-trash true
org.gnome.shell.extensions.dash-to-dock show-windows-preview true
org.gnome.shell.extensions.dash-to-dock transparency-mode 'DEFAULT'
org.gnome.shell.extensions.dash-to-dock unity-backlit-items false
org.gnome.shell.extensions.dash-to-dock workspace-agnostic-urgent-windows true

```
The keys are colored red...

---

