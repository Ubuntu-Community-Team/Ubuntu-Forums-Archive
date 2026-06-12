---
title: "Some problems with Ubuntu/Kubuntu/Xubuntu/Lubuntu/Linux Mint/Debian"
date: 2014-05-18
forum: General Help
---

### Post by Christophe_Rose on 2014-05-18
Hi everyone! So I'm kinda new to Linux Forums and please tell me if I'm in the wrong section, thanks!

So here's my problem: I am using an Acer Aspire One 7540-5980 _(_[Click me for the specifications)]("http://www.cnet.com/products/acer-aspire-7540-5980-17-3-turion-ii-m500-windows-7-home-premium-64-bit-4-gb-ram-500-gb-hdd/") and i am getting several problems on systems from Debian to Ubuntu to Linux mint. Some of the problems are repaired by using Ubuntu 12 LTS but not alls so here's the list of problems with hope that someone will try to help me! :3 (never had any problems like these on windows sadly because i'm really looking forward to getting Linux 100%)

ALPS Touchpad: The Y (up down) sensitivity is higher than the X (left right) sensitivity so it's really annoying to use it.
ALPS Touchpad: I can turn off the touchpad, but can't turn it back on
Keyboard Hotkeys (FN or switch like bluetooth or wifi): Several of them doesn't works and when pressing bluetooth it shows the screen brightness (Keyboard, go home you're drunk)
Don't worry, as my problems goes i'll keep informed!

---

### Post by mastablasta on 2014-05-19
touchpad issue 1 - try changing sensitivity in touchpad settings. probably somewhere in system settings
touchpad issue 2 - might be a bug - i can't even turn it off - for some reson it doesn't work - my guess is unsupported firmware
keybaord Fn issue - have a similar issue on different laptop. i wonder what they did in kernel to mess up all this stuff. things to try (at leats in Kubuntu) is to check if correct keyboard layout is selected). if osme keys are nto working there is a workarround. i used the windows key to set them up to act instead of Fn key. for some reaosn they work in 12.04 but sotpped in 13.10 and even less work in 14.04.

there is a couple of other things you can try befor eworarround. one is to use boot option to disable ACPI. although i am not sure what that would mean for hibernaiton and simialar.

what makes me sad and upset is that certified hardware suddenly has so many issues. it's not just one issue i encountered with new version. it's many. :-(

---

### Post by Christophe_Rose on 2014-05-19
Thanks for your answer. Yes the've really messed up this time because with my Aspire One 722 or my Hp Pavillion p6 i've never had any problems. I've tryed the sensivity settings but still does nothing. I hope the fix it soon.

---

### Post by grahammechanical on 2014-05-19
Developers do change key bindings for their own reasons - to avoid conflicts with what they want the keyboard function keys to do. There will be a Keyboard utility that will give access to keyboard shortcuts and we can see what key combinations have been assigned to what functions. I do not see in 14.04 Keyboard utility any reference to direct Fn key function but only when combined with the Alt key. That sort of thing. I think that a lot will depend upon what keyboard layout we told Ubuntu we were using. My layout is generic so my function keys work as typical Linux function keys.

There may also be settings in the computer BIOS/UEFI that can enable or disable certain function key operations.

Regards.

---

### Post by Christophe_Rose on 2014-05-19
Alright then, i will try to replace FN with windows keys ^^'
But the main problem is the Alps touchpad... :/

---

