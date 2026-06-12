---
title: "Fn keys only work when battery installed!?"
date: 2016-09-03
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-09-03
I setup Ubuntu Mate 16.04 on a Lenovo G50-30
I was setting up a laptop for a friend last night, making sure i had everything working
when i got to testing what fn keys worked i was amazed every single one of them did something close to what they should
only exception being one that mostly works (basically does the same actions as alt tab but with 1 key so it acts as if you are holding the tab key)
when i press a fn key the system sees a key combo is being pressed eg <ctrl><alt><tab>
this morning when i got up i removed the battery and powered it up found out the 4.7 kernel may have a fix for the wifi issue i had worked around
when testing the 4.7 kernel my fn keys did not work, about 30 minutes later trying to reproduce when they were working i put the batter back in and surprise they work again

Is this some hardware level implementation for fn keys? or something that can be controlled via software?

---

### Post by mook765 on 2016-09-03
This is another difficult chapter...
Some basic background:
When you hit a key on the keyboard, you mostly want that something happens.
The operating system has to make a decision what should happen.
This decision has to pass different levels.

Level1:
When you hit a key, the keyboard will generate a scancode and send it to the operating system
For example we hit the "A"-key. The keyboard will send the scancode 1e9e, where 1e is generated when
the key is pressed down and 9e is generated when the key is released.

Level2:
The operating system will map the scancode to a keycode. In our example we will get the keycodes
30 press
30 release
Mapping the scancodes to keycodes oblies the kernel.

Level3:
The keycode will be mapped to an action.
In our example it will output the letter a, it could be "A", it could be a chinese letter or something
else. This depend on your current layout and on the state of modifiers (like the shift-key is one)
It could be an action, for example a program could be started, all this depends on modifiers.

We have influence only upon Level2 and Level3.
Level1 is keyboard-intern, we don't have any influence upon that.

So now we come to your case.
We can check if  a key results in a scancode with the command
```
sudo showkey -s
```
If you detach the battery and run this command, then hit the fn-key, you can see if a scancode is sent
to the operating system or not.
If hitting the key doesn't result in a scancode then nothing can be done, this is a keyboard-internal thing.
It may depend on the hardware or the software which is called firmware...
If you get a scancode it might be a very strange code which is not known by the operating system and can't
be mapped to a keycode. Then you have the chance to do something. You could define a rule how to map this
scancode to a keycode which should be the normal keycode of the fn-key.
How to define this rule is another chapter which i didn't figure out yet.
I suggest to keep the battery attached to the laptop...

---

### Post by pqwoerituytrueiwoq on 2016-09-03
no response without battery, thanks
ok time to hack the firmware, ok im joking now that is too much work that i don't know how to do and risk flashing it with broken firmware

---

