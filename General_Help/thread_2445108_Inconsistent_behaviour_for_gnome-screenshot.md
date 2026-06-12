---
title: "Inconsistent behaviour for gnome-screenshot"
date: 2020-06-09
forum: General Help
---

### Post by gabbello on 2020-06-09
Hello,

I have a fresh ubuntu 20.04 installation and have some issues with  gnome-screenshot, particularity with "Select are to grab" option. 

Please note that I changed the shortcut key for this option, but I'm not sure how this could generate this behavior (as it doesn't only happen when using shortcut key).

It seems that **sometimes** the screenshot tool does not copy the selected area.
 
I know that it did not copy it when I don't hear the "click" sound after I select the area, however sometimes it works. 


If I try it from command line:
```
gnome-screenshot -a -c
```

it does not return any error (or success for when it works). Is there a way to increase verbose level?

If I use the interactive tool: 
```
gnome-screenshot -i
```

I noticed that when it does not work I'm not shown the new window (choose action: Copy to clipboard or Save, I'm simply returned to previous gnome-screenshot window)

Note that I'm also using Clipboard indicator (for managing clipboard), but I had the same setup on 18.04. Have no idea what other log file I could look into.

---

### Post by Dennis N on 2020-06-09
My feeling is that it fails when you do too much "adjusting" of the selected area (excessive cursor movement). I've learned to have a good notion of what I want to capture, start at upper left and go straight to lower right. If you are viewing something with Firefox, it has a good screenshot tool built in. Try that.

---

### Post by gabbello on 2020-06-10
Doesn't look that this is the case, even if I don't move the mouse and do the very basic selection, I still have this issue, these seem to be the error from /var/log/syslog

```
JS ERROR: TypeError: this._dialog is null#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012pushModal@resource:///org/gnome/shell/ui/main.js:549:18#012_takeModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:209:23#012grab@resource:///org/gnome/shell/ui/grabHelper.js:182:19#012grabAsync/<@resource:///org/gnome/shell/ui/grabHelper.js:201:23#012grabAsync@resource:///org/gnome/shell/ui/grabHelper.js:198:16#012selectAsync@resource:///org/gnome/shell/ui/screenshot.js:332:32#012SelectAreaAsync@resource:///org/gnome/shell/ui/screenshot.js:241:50#012_handleMethodCall@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:371:35#012_wrapJSObject/<@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:404:34
Jun 10 15:45:53 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: message repeated 1002 times: [ JS ERROR: TypeError: this._dialog is null#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012pushModal@resource:///org/gnome/shell/ui/main.js:549:18#012_takeModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:209:23#012grab@resource:///org/gnome/shell/ui/grabHelper.js:182:19#012grabAsync/<@resource:///org/gnome/shell/ui/grabHelper.js:201:23#012grabAsync@resource:///org/gnome/shell/ui/grabHelper.js:198:16#012selectAsync@resource:///org/gnome/shell/ui/screenshot.js:332:32#012SelectAreaAsync@resource:///org/gnome/shell/ui/screenshot.js:241:50#012_handleMethodCall@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:371:35#012_wrapJSObject/<@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:404:34]
Jun 10 15:45:53 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: null has no properties#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012pushModal@resource:///org/gnome/shell/ui/main.js:549:18#012_takeModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:209:23#012grab@resource:///org/gnome/shell/ui/grabHelper.js:182:19#012grabAsync/<@resource:///org/gnome/shell/ui/grabHelper.js:201:23#012grabAsync@resource:///org/gnome/shell/ui/grabHelper.js:198:16#012selectAsync@resource:///org/gnome/shell/ui/screenshot.js:332:32#012SelectAreaAsync@resource:///org/gnome/shell/ui/screenshot.js:241:50#012_handleMethodCall@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:371:35#012_wrapJSObject/<@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:404:34
Jun 10 15:45:53 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: message repeated 3570 times: [ JS ERROR: TypeError: null has no properties#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012pushModal@resource:///org/gnome/shell/ui/main.js:549:18#012_takeModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:209:23#012grab@resource:///org/gnome/shell/ui/grabHelper.js:182:19#012grabAsync/<@resource:///org/gnome/shell/ui/grabHelper.js:201:23#012grabAsync@resource:///org/gnome/shell/ui/grabHelper.js:198:16#012selectAsync@resource:///org/gnome/shell/ui/screenshot.js:332:32#012SelectAreaAsync@resource:///org/gnome/shell/ui/screenshot.js:241:50#012_handleMethodCall@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:371:35#012_wrapJSObject/<@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:404:34]
Jun 10 15:45:53 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: null has no properties#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9
Jun 10 15:45:54 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: message repeated 4573 times: [ JS ERROR: TypeError: null has no properties#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9]
Jun 10 15:45:56 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: windowActor is null#012_addWindowEffect@resource:///org/gnome/shell/ui/closeDialog.js:90:28#012vfunc_show@resource:///org/gnome/shell/ui/closeDialog.js:162:14
Jun 10 15:46:01 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: windowActor is null#012_addWindowEffect@resource:///org/gnome/shell/ui/closeDialog.js:90:28#012vfunc_show@resource:///org/gnome/shell/ui/closeDialog.js:162:14
Jun 10 15:46:04 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: this._dialog is null#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012popModal@resource:///org/gnome/shell/ui/main.js:589:22#012_releaseModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:228:14#012ungrab@resource:///org/gnome/shell/ui/grabHelper.js:275:18#012onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:326:18#012_onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:13:23
Jun 10 15:46:04 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: message repeated 1003 times: [ JS ERROR: TypeError: this._dialog is null#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012popModal@resource:///org/gnome/shell/ui/main.js:589:22#012_releaseModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:228:14#012ungrab@resource:///org/gnome/shell/ui/grabHelper.js:275:18#012onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:326:18#012_onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:13:23]
Jun 10 15:46:04 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: null has no properties#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012popModal@resource:///org/gnome/shell/ui/main.js:589:22#012_releaseModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:228:14#012ungrab@resource:///org/gnome/shell/ui/grabHelper.js:275:18#012onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:326:18#012_onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:13:23
Jun 10 15:46:04 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: message repeated 3571 times: [ JS ERROR: TypeError: null has no properties#012_onFocusChanged@resource:///org/gnome/shell/ui/closeDialog.js:135:9#012popModal@resource:///org/gnome/shell/ui/main.js:589:22#012_releaseModalGrab@resource:///org/gnome/shell/ui/grabHelper.js:228:14#012ungrab@resource:///org/gnome/shell/ui/grabHelper.js:275:18#012onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:326:18#012_onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:13:23]
Jun 10 15:46:06 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: windowActor is null#012_addWindowEffect@resource:///org/gnome/shell/ui/closeDialog.js:90:28#012vfunc_show@resource:///org/gnome/shell/ui/closeDialog.js:162:14
Jun 10 15:46:11 olga-Lenovo-ideapad-500S-13ISK gnome-shell[2583]: JS ERROR: TypeError: windowActor is null#012_addWindowEffect@resource:///org/gnome/shell/ui/closeDialog.js:90:28#012vfunc_show@resource:///org/gnome/shell/ui/closeDialog.js:162:14
Jun 10 15:46:17 olga-Lenovo-ideapad-500S-13ISK slack.desktop[2916]: [06/10/20, 15:46:17:413] info: [API-Q] (T02FT78HP) 81fdb383-1591793177.408 search.autocomplete.querySuggestions called with reason: no_reason_provided

```

---

### Post by ActionParsnip on 2020-06-10
Could use imagemagick and run:

```

sleep 10; DISPLAY=:0 import -window root

```

The sleep command gives you 10 seconds to arrange the screen. You can even use this over SSH to snap the screen of a remote system :)

---

