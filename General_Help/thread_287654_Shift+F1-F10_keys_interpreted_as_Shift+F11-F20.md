---
title: "Shift+F1-F10 keys interpreted as Shift+F11-F20"
date: 2006-10-29
forum: General Help
---

### Post by danyul on 2006-10-29
Hi all,

I've been trying to get either my context menu key or the ostensibly synonymous Shift-F10 combination working on Edgy, with no success. (Shift-F10 is supposed to bring up the context menu as if you had right-clicked on something in such applications as OpenOffice.org and Thunderbird.)

I finally found out kinda what might be going on- I went to Preferences->Keyboard Shortcuts, and tried binding Shift-F10 to one of the actions there.  When I hit Shift-F10 it shows up as Shift-F20!  In fact, all of the Shift-Fx key combinations are shown as Shift-F(x+10).  This is not the case for Control-Fx key combinations or plain Fx keys with no modifying key.

As it is, Shift-F10 and the context menu key do not work at all when in Gnome.  The only exception is if I load a VMWare Windows XP session- then both the context menu key and Shift-F10 work fine.

I am running Edgy/Gnome/XGL/Beryl; I've disabled the Beryl keybindings that use Shift F10.

Does anybody have any advice on how I can get OpenOffice.org or Thunderbird to receive the Shift-F10 (or, if possible, the Context Menu Key) signal?

Thank you very much!

Best,
Dan

---

### Post by fenallen on 2006-10-30
Hi there,

I am also having problems with F-keys and having read your post I checked Shift-F10 on my system - sure enough it shows up in 'System/Keyboard Shortcuts' as Shift-F20.

My issue lies with F10 on its own.  Although it shows up in 'System/Keyboard Shortcuts' correctly it appears to be interpretted in other places as your elusive Shift-F10.

I use midnight commander(mc) for all file tasks and have done so for years and years.  mc makes use of F10 and therefore the gnome terminal menu shortcut key (which also uses F10) needs to be disabled (edit/keyboard shortcuts).  This is usually no problem but edgy is behaving strangely:

Having disabled it I no longer get the gnome terminal F10 interpretation which would give me the gnome terminal menu items but rather the right click context menu.  Now the default keyboard shortcut in gnome is Shift-F10.  

This little bug means I can currently not use gnome terminal and I am using konsole instead.

These 2 issues must surely be related.

---

### Post by danyul on 2006-10-30
Hi Fenallen et al,

I was able to address most of my keyboard issues through the use of the following commands:

xev - lets you see info on what the computer is actually seeing at a low level

xkeycaps - gives you a gui to help you switch around keys and do other binding voodoo

xmodmap - lets you remap keys, from the command line

With these three I was able to solve nearly all my keyboard woes.

I also found the xbindkeys / xbindkeys-config commands quite useful for launching applications with key presses.

---

