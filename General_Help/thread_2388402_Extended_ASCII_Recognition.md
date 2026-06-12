---
title: "Extended ASCII Recognition"
date: 2018-04-02
forum: General Help
---

### Post by lawrence-joy on 2018-04-02
Why doesn't Ubuntu recognize extended ASCII, such as ALT 2-3-4 to get upper case Omega? Is there a workaround?

---

### Post by Impavidus on 2018-04-02
I don't know which encoding puts upper case omega at 234 (is that octal, decimal or hexadecimal?), but you can enter an upper case omega. [It's at hexadecimal code 3A9]("https://en.wikibooks.org/wiki/Unicode/Character_reference/0000-0FFF"), so you can enter it with ctrl+shift+u, 3, a, 9, <space>: &#937;. Instead of space, you can terminate the code by hitting enter or by holding ctrl+shift until finished (unless your text editor does something else when you hit ctrl+shift+a).

Some legacy 8-bit encodings may put upper case omega somewhere in the range 80&#8211;FF. Nowadays everyone uses Unicode, in the Linux world in UTF-8 encoding. You can convert text files encoded in old 8-bit encodings: [https://stackoverflow.com/questions/64860/best-way-to-convert-text-files-between-character-sets](https://stackoverflow.com/questions/64860/best-way-to-convert-text-files-between-character-sets)

---

### Post by The Cog on 2018-04-02
I'm mildly curious to know what kind of system used to use Alt 2,3,4 to generate omega. An archaic windows at a guess, but I can't quickly find a matching code page. By "exended ASCII" I assume this refers to an 8-bit encoding scheme. 

Note that as well as being able to use ctrl-shift-u followed 4 hex digits for the unicode value there is a fascinating GUI utility called Character Map (it's installed by default in Xubuntu, don't know about the other versions) that shows you the whole unicode set. You can double-click characters to add them to the text field at the bottom where you can use the GUI copy function then paste then into your app.

---

### Post by lawrence-joy on 2018-04-07
I think the 234 is decimal. In doing an Internet search it shows the 234 without telling if it is decimal, octal, hexadecimal, or whatever. You have to use the keypad numbers and not the numbers on the upper row of keys on the keyboard. When I use my Windows 10 system and I compose a text message in Yahoo Mail this works. When I use my Ubuntu system and compose a text message in Yahoo Mail the Alt 2-3-4 doesn't do anything. I'll look on the Internet for UTF-8 encoding.--Thanks.

---

### Post by lawrence-joy on 2018-04-07
I opened up my Yahoo Mail under my Ubuntu OS and tried entering Ctrl+Shift+u (because you are holding down the Shift key this would be an upper case U). This brings up a "File Upload" window. So that didn't work.

---

### Post by Impavidus on 2018-04-08
Does it work in other applications? I suspect that your browser/your website defines some conflicting meaning for ctrl+shift+u. I suspect there's some way to block that, but I don't know how.

---

### Post by lawrence-joy on 2018-04-09
I don't know if the Ctrl-Shift-u works in any other application besides Yahoo Mail. The only other application I am interested in, and why I loaded Ubuntu on my separate solid state drive, was to use KiCad schematic capture and printed circuit board layout program. I'll have to see if the Ctrl-Shift-u works there. The browser I use with Ubuntu is Firefox.

---

### Post by The Cog on 2018-04-14
I just discovered that Ctrs-Shift-U was broken in my xubuntu system. I found that (in the terminal) Ctrl-Shift-U simply deleted to the beginning of the line. I don't know how long it's been that way, I don't use unicode input very often. But the fix I just used to get it working again was:
* install ibus (sudo apt install ibus), 
* reboot, 
* then in the GUI go to Settings, Language Support and change the Keyboard input method system to IBus, 
* reboot. 
You must release the Ctrl-Shift after the underlined _u_ appears. You don't need to type leading zeros, and you finish either space or enter. 
It works in firefox, terminal and LibreOffice - everything I tried except the tty1-tty6 consoles.
P.S. It also works in the password field as you first login to xubuntu.

UPDATE
Ooh, it's nowhere near as simple as I thought. I just moved to my laptop instead, and I find that Ctrl-Shift-U works on there (also xubuntu 18.04). And on there, the keyboard input method is None, and IBus is not an option. So clearly I have no idea what settings are actually needed for Ctrl-Shift-U to work. Both my desktop and laptop have both carried my user settings across many upgrades.

---

