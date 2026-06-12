---
title: "Mapping Alt+Arrows to send Home and End"
date: 2013-12-03
forum: General Help
---

### Post by androith on 2013-12-03
***Desired result:*** I want to press **Alt+RightArrowKey** to go to **End** (end of line) and **Alt+LeftArrowKey** to go **Home **(beginning of line).

***A valiant attempt:*** I heard claims that you can achieve this with xmodmap as follows:
[LIST=1]
[*]Obtain X11 key codes and key names for LeftArrow and RightArrow with [FONT=courier new]xev[/FONT] (e.g., I have KEYCODE: 114 KEYNAME: Right for pressing right arrow, and KEYNAME: End for pressing the End key)
[*]Obtain modifier key names with [FONT=courier new]xmodmap -pm[/FONT] (e.g., I have mod1 for left Alt)
[*]Use [FONT=courier new]xmodmap -e "keycode KEYCODE MODIFIER = behaviour behaviour_with_modifier"[/FONT] to get desired result (I should use [FONT=courier new]xmodmap -e "keycode 114 mod1 = Right End"[/FONT]). Here, one should use KEYNAME for behaviour.
[*]This **doesn't work :(**
[/LIST]
***How can I achieve my desired result?***

---

### Post by androith on 2013-12-03
[COLOR=#696969][/COLOR]Just kidding. The following didn't work in all applications :(
[COLOR=#696969]
Solved. Paste the following into ~/.xbindkeysrc

[FONT=courier new]"xvkbd -xsendevent -text '\[Delete]'"[/FONT]
[FONT=courier new]  Alt + BackSpace[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]"xvkbd -xsendevent -text '\[End]'"[/FONT]
[FONT=courier new]  Alt + Right[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]"xvkbd -xsendevent -text '\[Home]'"[/FONT]
[FONT=courier new]  Alt + Left[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]"xvkbd -xsendevent -text '\[Page_Down]'"[/FONT]
[FONT=courier new]  Alt + Down[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]"xvkbd -xsendevent -text '\[Page_Up]'"[/FONT]
[FONT=courier new]  Alt + Up

[/FONT]Then start [FONT=courier new]xbindkeys[/FONT]. Be sure to install xvkbd and xbindkeys first, via apt-get.[/COLOR]

---

