---
title: "All hotkeys of LibreOffice 4.1.2.3 don't work in non-English keyboard layout"
date: 2013-10-31
forum: General Help
---

### Post by maqtanim on 2013-10-31
Hotkeys (Ctrl+b, Ctrl+s etc) in LibreOffice are language dependent  and work in English language only. While writing in any other language  i.e. any Cyrillic, it's impossible to use hotkeys, they just don't do  anything. Switching to English input language enable hotkeys once again.  This is very frustrating as user needs to switch language to save  document, to make it bold, or italic, etc.


 This was not experienced in Ubuntu 13.04.


 **Steps to reproduce:**

1. System Settings > Text Entry.
2. Add another keyboard layout beside English [In my case it is Bengali (Probhat)]
3. Now launch Writer.
4. Switch the keyboard layout from English (US) to Bengali (Probhat) by pressing Ctrl+Space.
    5. Press Ctrl+B to change font weight to bold.

 
**Error:**
Font weight does not get changed.

 
**Expected:**
Font weight should change to bold.

 
**Note:**
none other system hotkeys work as expected. I.e. Ctrl+s to save, or Ctrl+b to subscript, or Ctrl+i to italic etc.

 
**Workaround:**
The only way is to -

1. change the keyboard layout to English

2. then press desired hotkey

  3. then switch keyboard layout back to Bengali.


 The issue is critical, as it make writer very slow for keyboard-only typing. 

[I've already submit the bug at launchpad.]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1246583") Any quick help/solution is much appreciable. Thanks.

---

### Post by elimitrani on 2014-02-15
as i replied here: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1246583](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1246583)

this is a good workaround for now:
[LEFT]
[/LEFT][COLOR=#333333][FONT=Ubuntu Mono]Using 13.10, Libreoffice 4.2, Gnome desktop[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]I found a workaround - after re configuring my keyboard settings using 'sudo dpkg-reconfigure keyboard-configuration' the Alt+Shift key combination for changing language works again.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]This caused the following affects:
Press Super+Space: language changes, gnome language change displays on center screen, top bar display changes, hotkeys in when in Hebrew layout don't work.
Press Alt+Shift: language changes, top bar display changes, hotkeys in when in Hebrew **do** work.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]*But* - when using Thunderbird I have this behavior:
Press Super+Space: language changes, gnome language change displays on center screen, top bar display changes, hotkeys work fine on both layouts.
Press Alt+Shift: top bar display changes language, hotkeys work fine, but language does not change back to Hebrew (keeps typing in English even when top bar displays Hebrew).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]So the workaround is as follows:
In LibreOffice - use Alt+Shift
In Thunuderbird - use Super+Space.[/FONT][/COLOR]

---

