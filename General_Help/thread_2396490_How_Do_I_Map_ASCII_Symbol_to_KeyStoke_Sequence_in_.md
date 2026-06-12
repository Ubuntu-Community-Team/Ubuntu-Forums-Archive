---
title: "How Do I Map ASCII Symbol to KeyStoke Sequence in 16.04"
date: 2018-07-16
forum: General Help
---

### Post by rebeltaz on 2018-07-16
I figured out how to map the degree symbol (°) as a keystroke sequence (e.g. hold WinKey and double press 'o') under Mate, but I cannot figure out how to do the same thing under Ubuntu 16.04 LTS. I found keyboard shortcuts under System>Settings, but that appears to only work for actual commands, not text insertion. Any help, guys and gals?

---

### Post by Impavidus on 2018-07-16
I don't use Ubuntu 16.04, but the thing you're looking for is called the compose key. I think that somewhere hidden in your keyboard settings is an option to set a compose key. It has a large set of predefined sequences to type many symbols. Actually creating new sequences is a bit more difficult.

---

### Post by rebeltaz on 2018-07-16
Yeah.... I saw mention of that elsewhere, but I can't find [Compose Key] anywhere in my settings.

---

### Post by Keith Myers on 2018-07-16
> **rebeltaz said:**
> I figured out how to map the degree symbol (°) as a keystroke sequence (e.g. hold WinKey and double press 'o') under Mate, but I cannot figure out how to do the same thing under Ubuntu 16.04 LTS. I found keyboard shortcuts under System>Settings, but that appears to only work for actual commands, not text insertion. Any help, guys and gals?
This was driving me crazy with Ubuntu 18.04.  What used to work with Ubuntu 16.04 and standard ASCII alt-codes no longer works with 18.04.  I found out how to do the (°) symbol in 18.04.  [Ctrl-Shift-u], then [b-0-Enter]

I never found a way to map to the keyboard settings.  Sure fouls up your muscle memory for all the -ALT-codes you've learned in the past.:)

---

### Post by rebeltaz on 2018-07-16
> **Keith Myers said:**
> This was driving me crazy with Ubuntu 18.04.  What used to work with Ubuntu 16.04 and standard ASCII alt-codes no longer works with 18.04.  I found out how to do the (°) symbol in 18.04.  [Ctrl-Shift-u], then [b-0-Enter]

I never found a way to map to the keyboard settings.  Sure fouls up your muscle memory for all the -ALT-codes you've learned in the past.:)

Wow. What a keystroke combination! OK... that worked, but good grief. Thank you for that. Now if I can just remember B0 is degrees! :)

---

### Post by Impavidus on 2018-07-17
Here is a help text on the compose key, but I'm not sure it's entirely up to date: [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

I'm not sure about alt codes. I thought that was a DOS/Windows feature. But on Ubuntu, ctrl+shift+u, hexadecimal code, space should work. Also a few variants. The codes for all characters are just the standard Unicode numbers, but they are in hexadecimal. I think Windows wants them in decimal, except that the numbers come from an obsolete code page which had the degree symbol at a different location.

I don't know about Ubuntu, but in Xubuntu there is a simple setting in the keyboard config to activate the compose key. It works for me on Xubuntu 18.04 and has worked for many releases before. Somebody using Ubuntu may know where to find the setting there.

BTW, we're talking about Unicode codes here. ASCII is the first 128-character subset of Unicode, but those can generally be typed directly from the keyboard.

---

### Post by Holger_Gehrke on 2018-07-17
One way to reassign keys in any *buntu that uses X11 is to use the command line tool 'xmodmap'. Details can be found in it's manual page ('man xmodmap'). Changes made that way are not persistent across reboots (that's intentional, if you mess up your keyboard using xmodmap you can just log out and back in and everything works again), so if you want to make them permanent you'll have to write a short script and autostart that after logging in.

The 'ctrl-shift-u' combo is for Unicode, the hexadecimal number you type after the key-combination is the code point.It is superior to the old Alt(or AltGr)+numbers-on-keypad method because it gives you access to all the thousands of characters in Unicode and not just the 256 characters in an old windows codepage.

A compose key is an alternate way of entering accented characters, sometimes found in keyboard layouts without 'dead keys'. You hold the compose key, type the accent and the letter and release compose, for example: hold compose - type °a - release compose gives å.

Holger

---

### Post by HermanAB on 2018-07-17
You should try Autokey for more sensible keyboard macros.

---

