---
title: "Screen keeps dimming"
date: 2013-07-13
forum: General Help
---

### Post by pretty_whistle on 2013-07-13
How do I fix this?

I have ubuntu 13.04, btw.

---

### Post by synaptix on 2013-07-13
I believe there is an option under Power (System Settings) that controls screen dimming.

---

### Post by pretty_whistle on 2013-07-13
> **synaptix said:**
> I believe there is an option under Power (System Settings) that controls screen dimming.

That's what I looked for but I dont see it.

There is no "power" per se' option in the menu but there is "settings manager".  I thought it would be there but its not.

?

---

### Post by varunendra on 2013-07-13
> **synaptix said:**
> I believe there is an option under Power (System Settings) that controls screen dimming.

"Dim Screen to save power" checkbox ??

Yeah, that was an easy access to the setting, unfortunately, not available in 13.04.

@ pretty_whistle,

I don't know an elegant way to control that setting in 13.04, but you can install "dconf-tools" to control it directly-
```
sudo apt-get install dconf-tools
```
Then open it from dash (**Dconf Editor**) and navigate to - **org > gnome > settings-daemon > plugins > power >** clear the checkboxes "**idle-dim-ac**" (to disable dimming on ac power) and "**idle-dim-battery**" (to disable dimming on battery power), **OR**, change "**idle-dim-time**" (in seconds).

---

### Post by pretty_whistle on 2013-07-13
> **varunendra said:**
> "Dim Screen to save power" checkbox ??

Yeah, that was an easy access to the setting, unfortunately, not available in 13.04.

@ pretty_whistle,

I don't know an elegant way to control that setting in 13.04, but you can install "dconf-tools" to control it directly-
```
sudo apt-get install dconf-tools
```
Then open it from dash (**Dconf Editor**) and navigate to - **org > gnome > settings-daemon > plugins > power >** clear the checkboxes "**idle-dim-ac**" (to disable dimming on ac power) and "**idle-dim-battery**" (to disable dimming on battery power), **OR**, change "**idle-dim-time**" (in seconds).
Thanx... I'll try that.

---

### Post by pretty_whistle on 2013-07-13
> **varunendra said:**
> "Dim Screen to save power" checkbox ??

Yeah, that was an easy access to the setting, unfortunately, not available in 13.04.

@ pretty_whistle,

I don't know an elegant way to control that setting in 13.04, but you can install "dconf-tools" to control it directly-
```
sudo apt-get install dconf-tools
```
Then open it from dash (**Dconf Editor**) and navigate to - **org > gnome > settings-daemon > plugins > power >** clear the checkboxes "**idle-dim-ac**" (to disable dimming on ac power) and "**idle-dim-battery**" (to disable dimming on battery power), **OR**, change "**idle-dim-time**" (in seconds).
Cool.  That fixed it.

Also, for others who may need to know, Dconf was already installed.  You can find it in "System" on the Applications Menu (This is on the Xfce desktop).

---

### Post by varunendra on 2013-07-13
> **pretty_whistle said:**
> Cool.  That fixed it.

Also, for others who may need to know, Dconf was already installed.  You can find it in "System" on the Applications Menu (This is on the Xfce desktop).

Great! And I just cross-checked on my live dvd of 13.04 (default one with unity) and can confirm that dconf-editor is installed by default. A compensation for hiding those settings maybe ? :P

---

