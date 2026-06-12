---
title: "Alt+PrintScreen"
date: 2013-08-16
forum: General Help
---

### Post by Newbunto on 2013-08-16
I am trying to use Alt+PrintScreen to save an image of the current window to a file. For the purposes of testing I am using nautilus as the window.

Sometimes it works - but after it has worked the launcher comes up saying "Type your command". Most of the time it does not work. When it does not work, most of the time I get an image of the entire screen i.e. as if I had not pressed Alt, and the launcher comes up saying "Type your command". Sometimes when it does not work I get an image of the launch bar!

Ubuntu is 12.04

Use of PrintScreen seems to be launching something running "gnome-screenshot". Use of Alt+PrintScreen seems to be launching something running "gnome-screenshot --window".

Looking at Settings/Keyboard/Shortcuts/Screenshots I have the following assignments

Take a screenshot                    Print
Take a screenshot of a window   Alt+Print
Take a screenshot                    Print
Take a screenshot of a window   Alt+Print
Take a screenshot of an area     Shift+Print
Copy a screenshot to clipboard etc.

I don't know why the first two shortcuts are repeated, but the shortcut assignments seem to be correct other than that. However because the shortcuts are repeated if I wanted to change the shortcut, I am not sure which one to change.

I have read some posts that talked about SysRq. I don't know whether it is interfering or whether it is even enabled.

I don't know whether it is relevant but I am using a laptop but with  external mouse, keyboard and monitor. Opening the laptop lid and doing  it on the laptop keyboard and screen doesn't seem to make any  difference.

---

### Post by coldraven on 2013-08-16
On my laptop I have to press Fn+prtsc for full screen or Alt+Fn+prtsc for the current window.

Edit: I forgot to add that I'm using 12.10 with the default Unity settings. I just checked and they are the same as yours.

---

### Post by Newbunto on 2013-08-19
Opening the laptop lid and trying *that* key combination doesn't help either. Still gives crazy inconsistent behaviour and works incorrectly most of the time.

The fact that the configured key sequence does work sometimes makes me think that the solution is not to press a different key sequence.

---

### Post by Newbunto on 2013-09-04
bump

---

### Post by Newbunto on 2013-11-11
Upgraded to Ubuntu 13.10

Unfortunately still the same result. :sad:

Looking at Settings/Keyboard/Shortcuts/Screenshots, the duplicates have at least disappeared.

I may have found a workaround. Press and hold Print Screen. Please and hold Alt. Release Print Screen. Release Alt.

Pressing Alt first (which one would more naturally do) now *always* seems to result in a printscreen of the launcher prompting me to "type your command" i.e. less functional than before but more consistent.

Pressing and releasing Alt seems to bring up the same prompt. But I couldn't find any way to disable (or assign a different key to) that function.

---

### Post by mc4man on 2013-11-11
Alt for Hud is a continuing issue, sometimes gets in the 'way',  sometimes not. (currently here on 14.04 dev it's not an issue.

Anyway I have no use for Hud so always end up disabling it altogether. To do that it's in dconf-editor, scr. 1, or  unityshell plugin settings in ccsm (compizconfig-settings-manager, screen 2,  (click on the bindings box > disable
or just use gsettings - 
```
gsettings set org.compiz.integrated show-hud "['Disabled']"
```

---

### Post by Newbunto on 2013-11-12
Awesome. That command does it. I too can live without "Alt" to bring the hud up. I only use it occasionally and am happy to click on the launcher when I do need it.

I guess I should have checked this first but what was the setting before - in case I want to change it back? In other words, what command would restore the previous behaviour?

---

### Post by mc4man on 2013-11-12
> **Newbunto said:**
> Awesome. That command does it. I too can live without "Alt" to bring the hud up. I only use it occasionally and am happy to click on the launcher when I do need it.

I guess I should have checked this first but what was the setting before - in case I want to change it back? In other words, what command would restore the previous behaviour?

```
gsettings set org.compiz.integrated show-hud "['<Alt>']"
```

---

