---
title: "Apple Bluetooth Keyboard pairing on Hardy"
date: 2008-04-24
forum: General Help
---

### Post by msodrew on 2008-04-24
[B]EDIT: UNSOLVED: OK so I was unaware that you can do hidd --connect <MAC-ADDRESS-OF-APPLE-KEYBOARD>, then you press a 4 digit code and return, THEN you use a regular usb wired keyboard and enter in the same code and hit enter. Geez, linux makes it so obfuscated.
[/B]
[I]Hey so I've googled around a TON and have seen other threads but still can't seem to get my Apple Bluetooth Keyboard (the short one without a numpad) to pair with 8.04 Hardy.

I tried getting rid of bluez-* completely (now there are no bluetooth tools whatsoever), tried pairing from the applet, tried pairing from the command line using hidd --search and dbus-send etc etc... to no avail!

Has anyone else had success getting an Apple Keyboard to pair in hardy? the OS "sees" the keyboard just fine, but then when prompted to pair, the popup from the applet comes, you click "Pair" and then it says to Enter in the pairing key with a blank window.

Am I supposed to type in my login password, or something else? How do I type up a blank string? I've tried just doing a generic 8-digit 0000 0000 then return type of thing that I'm used to for bluetooth devices but, again, no luck.

Please help![/I]

---

### Post by teqqan on 2008-04-24
Actually, you have to press a 8-16 digit code.

---

### Post by msodrew on 2008-04-24
Uh yeah so it doesnt work anymore. Paired once, never worked again. Now ubuntu cant even see the keyboard when using the bluetooth preferences menu. I've even unpaired and untrusted the keyboard, rebooted, nothing.


Bluetooth sucks so hard on ubuntu.

---

### Post by RLovelett on 2008-05-07
Why did this change from Gutsy to Hardy?  This was a terrible idea to be put into a release that is supposed to be stable.  My keyboard paired just fine in gutsy through the bluetooth manager, it never asked for a key or anything it just worked.  Now it's asking for keys and stuff, and it never really pairs with the keyboard.

Now you have to go the command line to get it to work some of the time.  They need to revert the repos to the bluez from gutsy until someone tests this stuff and it works.  Then put it into hardy.

Anyway, did anyone else find anything to help fix this permanently?

---

