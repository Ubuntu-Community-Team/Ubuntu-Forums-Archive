---
title: "I can't type special characters with disability keyboard &#9855;&#65039;"
date: 2021-11-21
forum: General Help
---

### Post by liam.gutierrez on 2021-11-21
Hi, sometimes I have to write in foreign languages and have to type special characters and accents. That's why I use the disability keyboard that pops up on screen when I enable it through universal access. It works flawlessly on my laptop but on my desktop, I can't type, for example, an "accent aigu" é or a German umlaut like ä.

Do I need to install the languages that use those letters/characters for it to work on disability keyboard?



                                                                                                     [SIZE=7]  :((((([IMG]https://ubuntuforums.org/attachment.php?attachmentid=289506&stc=1[/IMG][/SIZE]

---

### Post by Holger_Gehrke on 2021-11-21
If the on screen keyboard you're using happens to be 'onboard' then you should be able to get a pop up with international variants of a letter by keeping the mouse-button pressed (haven't managed to get it to do this with a touchpad and tap-to-click). On my system - which has keyboard layouts for German and American English - I get '&#324;ñn&#328;&#329;&#326;&#331;' in the pop up if I keep pressing the 'n' and those are letters that are not available in either layout.

If it is 'onboard' but the pop up doesn't appear you should look in the settings for onboard (right click on the icon for onboard in the notification area, select settings from the menu; in the form which appears select 'Keyboard' in the left panel, switch to the 'Advanced' tab in the right panel and set 'International character selection' as the 'Long press action'. It's also possible to set up your own 'keypad' - onboard is highly configurable - but this takes some doing.

Another tool to get characters that are not available on your keyboard - or any keyboard for that matter - is the 'character map' (gucharmap) which gives access to all of unicode and allows you to copy and paste strings of characters.

Holger

---

### Post by Impavidus on 2021-11-21
Other options for typing characters not found on your keyboard include ctrl+shift+u+(hexadecimal code) or compose sequences. Using those, there's no need to reach for the mouse, so it's normally faster. Of course, hexadecimal codes need some time to learn, but for simple accented characters, the compose sequences are very convenient.

---

### Post by liam.gutierrez on 2021-11-25
Thanks for the replies. 

I found a somewhat acceptable solution by installing the languages that use those characters: [B]Settings > Region & Language > Input Sources
[/B]I then clicked on **+** to install German.

Now I can type special characters like Umlaut "ö" by clicking/tapping on the globe key in the onscreen keyboard to switch from English to German

However, the language switch in the onscreen keyboard also affects my physical keyboard. It got a German layout. So, I have to switch back to English either in the settings or via the Globe button in the onscreen keyboard. Is there a way to change language only in the onscreen keyboard without messing up the physical keyboard?

---

### Post by Impavidus on 2021-11-25
I doubt it, but never tried the onscreen keyboard.

There are many ways to type accented characters and I think every solution that requires you to use the mouse is unacceptable, except for characters you use so rarely that you cannot memorise the efficient way to type them. Other options:
- Use a key to cycle through your selected keyboard layouts. For example: <menu> l <menu> &#8594; &#955;. Pro: easy if you want to type a lot of text in a different script. Contra: cycling through all layouts is too slow for a single character, as you may need many layouts to get to all characters. And it's hard to memorise many complete layouts.
- Several international layouts. These keep the normal actions of all keys the same, but many accented characters come available using the AltGr key (aka the right alt key). For example: AltGr+p &#8594; ö (as AltGr+o is already the ó). Pro: many accented letter available with just one additional modifier. Contra: not all of them are intuitively placed and, as they're usually not marked on the keyboard, they may be hard to memorise for characters you rarely need.
- A layout with dead keys. Hit the dead key with the accent, then the key with the letter to receive the accent. For example: ' e &#8594; é. Pro: very intuitive and easy to memorise. Contra: only some accented characters are available this way and you may loose the normal function of the dead keys.
- The compose key. Hit Compose, character 1, character 2, and you get something that looks like a composite of those characters. For example: Compose ^ w &#8594; &#373;. Pro: most simple accented characters are easy to memorise, many characters available. Contra: two additional keystrokes compared to the method using AltGr.
- Hexadecimal codes. Hit ctrl+shift+u, type the code, terminate with space or enter. Or hold ctrl+shift until you completed the hexadecimal code. For example: ctrl+shift+u e 6 <space> &#8594; æ. Pro: every unicode character is available. Contra: hard to memorise, many keystrokes required.

Use whatever you like; you don't have to stick to one of them. My personal favourite is the compose key.

---

### Post by liam.gutierrez on 2021-11-25
> **Impavidus said:**
> I doubt it, but never tried the onscreen keyboard.

There are many ways to type accented characters and I think every solution that requires you to use the mouse is unacceptable, except for characters you use so rarely that you cannot memorise the efficient way to type them. Other options:
- Use a key to cycle through your selected keyboard layouts. For example: <menu> l <menu> &#8594; &#955;. Pro: easy if you want to type a lot of text in a different script. Contra: cycling through all layouts is too slow for a single character, as you may need many layouts to get to all characters. And it's hard to memorise many complete layouts.
- Several international layouts. These keep the normal actions of all keys the same, but many accented characters come available using the AltGr key (aka the right alt key). For example: AltGr+p &#8594; ö (as AltGr+o is already the ó). Pro: many accented letter available with just one additional modifier. Contra: not all of them are intuitively placed and, as they're usually not marked on the keyboard, they may be hard to memorise for characters you rarely need.
- A layout with dead keys. Hit the dead key with the accent, then the key with the letter to receive the accent. For example: ' e &#8594; é. Pro: very intuitive and easy to memorise. Contra: only some accented characters are available this way and you may loose the normal function of the dead keys.
- The compose key. Hit Compose, character 1, character 2, and you get something that looks like a composite of those characters. For example: Compose ^ w &#8594; &#373;. Pro: most simple accented characters are easy to memorise, many characters available. Contra: two additional keystrokes compared to the method using AltGr.
- Hexadecimal codes. Hit ctrl+shift+u, type the code, terminate with space or enter. Or hold ctrl+shift until you completed the hexadecimal code. For example: ctrl+shift+u e 6 <space> &#8594; æ. Pro: every unicode character is available. Contra: hard to memorise, many keystrokes required.

Use whatever you like; you don't have to stick to one of them. My personal favourite is the compose key.

Thanks, I found this help page [URL="https://help.ubuntu.com/stable/ubuntu-help/keyboard-layouts.html.en"]https://help.ubuntu.com/stable/ubuntu-help/keyboard-layouts.html.en

[/URL]I find that the easiest solution as there are only minor differences in layouts and I can keep typing without using the mouse.

---

