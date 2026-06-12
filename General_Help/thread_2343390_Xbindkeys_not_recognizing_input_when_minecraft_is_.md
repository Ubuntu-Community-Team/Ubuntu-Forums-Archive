---
title: "Xbindkeys not recognizing input when minecraft is using the mouse. Workarou"
date: 2016-11-15
forum: General Help
---

### Post by irongolem0982 on 2016-11-15
[COLOR=#242729][FONT=Arial]In minecraft each hotbar slot has a default hotkey on the numeric keys at the top of the keyboard to allow quick switching to specific slots without having to scroll through all the slots.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Whilst in minecraft under Ubuntu (same behavior on windows, see below) you can bind the mouse browser forward and back hotkeys to hotbar slots and then "hotkey" to those slots later for like rod comboing and stuff.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The problem lies in that the MOUSE hotkeys do NOT work whilst in the inventory where the mouse is unbound. While the keyboard ones still work fine in both the inventory and the game.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
To get around this behavior on windows I simply installed [Xmouse Button Control]("https://www.highrez.co.uk/downloads/xmousebuttoncontrol.htm") and intercepted the keys and resent keyboard keys 1 and 2 which works great in both the inventory and the game.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I tried the same concept in Ubuntu using xbindkeys to detect mouse buttons then run xdotool key 1which worked like a charm in notepads and text boxes. But when I go into minecraft there is weird behavior:

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Whenever minecraft has the mouse locked xbindkeys does NOT recognize button presses. But whenever minecraft has it un-locked xbindkeys promptly recognizes the keypress and sends the command.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
So the functionality switches such that now it works in the inventory but not in the game.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]the overall goal I would like to achieve is functionality in both the inventory and the game.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
similar possible source of problem found here: [https://ubuntuforums.org/showthread.php?t=2111763](https://ubuntuforums.org/showthread.php?t=2111763)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I would like to be able to just play on windows but I never give up on Ubuntu and it runs better overall there anyway whilst recording. So y'all got any ideas? If need be I can re explain all of this on video to make it clearer..[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
other things I've tried:[/FONT][/COLOR]

[LIST]
[*]using xev instead of xdotool
[*]verified that minecraft does receive key presses from xbindkeys in both the inventory and the game.
[/LIST]

---

