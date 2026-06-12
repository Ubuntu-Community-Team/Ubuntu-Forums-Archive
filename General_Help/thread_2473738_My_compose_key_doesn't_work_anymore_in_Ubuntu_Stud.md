---
title: "My compose key doesn't work anymore in Ubuntu Studio 20.04 (with XFCE)"
date: 2022-04-12
forum: General Help
---

### Post by Federico_Esposito on 2022-04-12
My compose key suddenly stopped working few days ago, without me  doing anything, apparently. I set it to right ctrl, but it doesn't work  anymore. If I try another key (e.g. right alt), it doesn't work anymore.  Anyway the system recognizes that that key is "special" and will not  work for anything else (e.g. if right ctrl is set as compose key, I  cannot use it to select multiple items, it's exactly as a dead key).
 Running Ubuntu Studio: Ubuntu 20.04.2 LTS with XFCE 4.14 as desktop environment.

 **What I have tried**

 1. To set the compose key I edit the Settings > Keyboard > Layout, it just doesn't work. The rest of the layout settings are: [INDENT] 
Keyboard model: Generic 105-key PC (intl.)
 Change layout option: -
 Keyboard layout: English (US)
 [/INDENT]
[HR][/HR] 2. The file /etc/default/keyboard contains the following lines: 

 [FONT=courier new]# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS="compose:rctrl"

BACKSPACE="guess"[/FONT]

 I have tried to edit it directly or via the command sudo dpkg-reconfigure keyboard-configuration: I can edit it but the changes have no effect, the compose key still doesn't work (even after reboot).
 [HR][/HR] 3. I have read in many answers and comments about the files ~/.xsessionrc and ~/.xsession. I did not have these files (but I have the ~/.xsession-errors file), so I tried to create them and write a single line: 

[FONT=courier new]  /usr/bin/setxkbmap -option "compose:rctrl"[/FONT]
 
[HR][/HR] 4. The output of setxkbmap -query [FONT=arial]is :

[/FONT] [FONT=courier new]rules:      evdev
model:      pc105
layout:     us
options:    compose:rctrl[/FONT]
 
None of these methods worked. If you don't know how to fix my compose  key, do you know alternative ways to quickly digit accented letters? I  have a english keyboard on my laptop but I often have to write emails in  Italian or Spanish, and I need accented letters for those languages

---

### Post by tea for one on 2022-04-12
> **Federico_Esposito said:**
> If you don't know how to fix my compose  key, do you know alternative ways to quickly digit accented letters? I  have a english keyboard on my laptop but I often have to write emails in  Italian or Spanish, and I need accented letters for those languages

Using a UK keyboard, can you try this key combination:-

Press Alt Gr and Semi Colon simultaneously and then release.
Press a

Do you get á?

If it works, I'll dig out the complete list for Spanish characters.

---

### Post by Federico_Esposito on 2022-04-12
> **tea for one said:**
> Using a UK keyboard, can you try this key combination:-

Press Alt Gr and Semi Colon simultaneously and then release.
Press a

Do you get á?

If it works, I'll dig out the complete list for Spanish characters.


I assume AltGr = rightAlt (I don't have a AltGr key).
If I put

Keyboard layout: English (UK) 

and I simultaneously press 

rightAlt + ; + another random key

it produces weird characters, but no accented letters.
The above combination for qwertyuiopasdfghjklzxcvbnm returns @&#322;e¶&#359;&#8592;&#8595;&#8594;øþæßð&#273;&#331;&#295;&#312;&#322;«»¢“”nµ

But I have to press all 3 keys simultaneously. If I release after pressing rightAlt + ; it has no effect at all, and the following key returns the usual character.

---

### Post by tea for one on 2022-04-12
> **Federico_Esposito said:**
> I assume AltGr = rightAlt (I don't have a AltGr key)

I think (although not 100% sure) that the [COLOR="#0000FF"]Alt Gr[/COLOR] key may be the important clue.

A bit more info [https://en.wikipedia.org/wiki/AltGr_key](https://en.wikipedia.org/wiki/AltGr_key)

---

