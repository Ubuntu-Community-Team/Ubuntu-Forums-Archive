---
title: "IBM &quot;Rapid Access&quot; keys in Xubuntu"
date: 2007-07-19
forum: General Help
---

### Post by UJoe4 on 2007-07-19
I have one of those IBM "Rapid Access" keyboards (with the colored application buttons along the top) and I want to assign keyboard shortcuts to them in Xubuntu Feisty. Following tips from old threads, I've been able to get special keys on other keyboards to work by running "xev", noting the keycodes the keys return, binding them to F13-F35 using xmodmap, and then assigning keyboard shortcuts to F13-F35.

The problem is that only about half of the special keys on this keyboard return any keycodes at all in xev. And it seems pretty random: 2 of the application keys return codes and the other 4 don't, Volume-Down does but Volume-Up doesn't, etc. All the keys work in Windows so there's nothing physically wrong with the keyboard.

I've tried changing the keyboard layout in the Settings menu to each of the different Rapid Access versions but that didn't help.

Any ideas?

---

### Post by UJoe4 on 2007-07-20
Turns out that for whatever reason, half the keys weren't being translated into keycodes at all (at the kernel level). So they wouldn't show up in X no matter what program I used (xev, showkey, lineak...).

So I had to:

1) Look in dmesg after pressing those keys to see what their hexadecimal scancodes are;

2) make an init script to bind those scancodes to numerical (0-255) keycodes;

3) make an /etc/X11/gdm/PostLogin script to bind those numerical keycodes to Function keys; and

4) assign shortcuts to those function keys in the Xfce keyboard shortcut utility.

So, thanks to various old threads on this and other forums (the best one probably being [http://ubuntuforums.org/showthread.php?t=27039]("http://ubuntuforums.org/showthread.php?t=27039")), it works.

---

### Post by bob12564 on 2007-12-28
I have the same keyboard and the same problem with the multimedia keys.

I am a complete Linux/Ubuntu newbie. I've been playing with the Live CD for v7.10 this week to see what works and what doesn't work and to determine if Ubuntu is for me.

I've read the threads on the keyboard issues but most of it is over my head at this point.  One fundamental question I have is why these keys don't work once the correct keyboard is selected in System menu -> Preferences -> Keyboard?  For example, why does Calculator get assigned to "volume down"?  

In any event, for a newbie, would KeyTouch or Lineak be easy ways to get the multimedia keys working, including the one that don't get recognized in the kernal and don't produce scancodes when pressed?  Or would you recommend that I give up on the keyboard for a while until I understand Linux enough to follow your solution?

Thanks!

---

