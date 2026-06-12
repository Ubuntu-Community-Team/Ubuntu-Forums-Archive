---
title: "[SOLVED] Backslash/PIPE key problems (cannot find answer anywhere)"
date: 2007-12-26
forum: General Help
---

### Post by warnox on 2007-12-26
Hey!

I've just installed Ubuntu, well about 2 hours ago and this is one problem that I cannot seem to find the answer to anywhere!

I have a:
NEC Versa E2000 laptop

When installing Ubuntu I chose US. English as my default language and in my keyboard preferences the default language is **US English (default)** and the keyboard model is **Generic 105-key (Intl) PC**.

Everything on the keyboard seems to work fine except this one key! The key is located between the LEFT Shift key and the Z key. Normally when I press the key backslash is supposed to show up and when i press SHIFT+theKey the PIPE symbol is supposed to show up. But in Ubuntu when I either get < or >. No idea why.

I've looked in and edited the **/etc/X11/xkb/sybmols/us** file and tried adding a line for this key but it doesn't seem to do anything.

key <BKSL> { [ backslash,        bar ] }; ---------- is the line I tried adding but it didn't do anything. Although if I change another line from say 'z' to 'backslash' it does work. For some reason I cannot add this key in or find it anywhere...

Any help appreciated,

Thank you



Gregor

---

### Post by SPr on 2007-12-26
Have you tried changing the keyboard layout? System>Preferences>Keyboard

---

### Post by kuja on 2007-12-26
I would probably try to xmodmap it .... to do so:

Use xev to obtain the keycode of both the backslash and the pipe (just run xev in a terminal and push the key(s). It'll print out a bunch of info including the keycode, hopefully it won't be the same as that of your real <> keys.)

Assuming it's not the same keycodes as your real <> keys, create a file ~/.xmodmaprc

add lines like  this to it using the keycodes that you obtained from xev

> keycode 51 = backslash
keycode 50 = bar

Then run the command xmodmap ~/.xmodmaprc and see if your key is working.I suspect that would do it but I make no guarentees. 

Only problem I can see with this approach is that it is rather GUI dependent and probalby won't want to work at all in a tty.

---

### Post by warnox on 2007-12-26
Thanks for your help!

---
Yes I did try changing the keyboard layout but really have no idea what one to choose, there is no NEC keyboards available on that list...
---

I used 'xev' to obtain the keycodes and turns out they are the same for < and > on both sides! So adding them to xmodmap would just create more problems.

Also I forgot to mention, I had this same problem with Debian.

Any more ideas welcome...

---

### Post by warnox on 2007-12-26
Does no one else really have any idea?

---

### Post by MrFred on 2008-01-16
here is the procedure (and excuse my not-so-perfect english) :

First use xev in a terminal to find the keycode of your key:

press \, it will answer something like : 
[CENTER][SIZE="1"]
KeyPress event, serial 30, synthetic NO, window 0x3200001,
    root 0x75, subw 0x0, time 2201988370, (341,214), root: (346,263),
    state 0x2010, [COLOR="Red"]keycode 51[/COLOR] (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XmbLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False[/SIZE][/CENTER]

One touch is one keycode so it's ok if | and \ have the same keycode.
Then edit a file (its name does not matter) say:

gedit ~/.xmodmap

and put the following line in this file

keycode 51 = backslash bar

Where you replace your keycode number (51 here) by the one xev gave you. The two arguments tell xmodmap to react differently when the SHIFT keys are pressed.

Then launch xmodmap with your created file

xmodmap  ~/.xmodmap

---

### Post by warnox on 2008-01-20
Thanks for your help, but I have finally solved this problem, here is how!

---
I did use 'xev' to find out what keycode the '\' and '|' were printing, they were both doing KeyCode 94, not sure why! The characters they were printing were '<' and '>' respectively.

I had a look at my current keymap with 'xmodmap -pke' and it showed that KeyCode 94 was:
'**keycode 94 = less greater bar brokenbar bar brokenbar**'.

I didn't just want to go ahead and change keycode 94 to 'bar brokenbar' just in case that would make the actual '<' and '>' keys not work. So I checked what keycode they were printing and it was keycode 59 and keycode 60.

So I figured I can go ahead and change keycode 94, I did this with:
**xmodmap -e 'keycode 94 = backslash bar'**

This seemed to work, and now everything seems to work fine.

---

Mr. Fred: I did see that KeyCode 51 does say 'backslash bar' but I do not know how to get that particular key to relate to KeyCode 51, that is why I went ahead and changed KeyCode 94, since that is what it is pointing to.

If you know how I can change this please let me know :)

Thanks again...

---

### Post by michael_mallett on 2008-06-10
Hi,
I've had the exact same problem only I also have an issue with my hash/tilde key
(strangely my bar error was 94 and my bar WAS set to 51 which is my hash/tilde key)
Anyhow, I cannot find the keysym value for the hash key anywhere and therefore I have no hash key:

mjm@mjm-ubuntu:~$ xmodmap -e 'keycode 51 = hash asciitilde'
xmodmap:  commandline:1:  bad keysym name 'hash' in keysym list
xmodmap:  1 error encountered, aborting.

I've looked in the current table (xmodmap -pke) but no entries correspond to hash and i've tested every key on the keyboard. Could someone please run xev and press their hash key and provide the keysym value for it ('equal' when pressing equals key, 'slash' when pressing forward slash etc) or run xmodmap -pke and lookup the hash value.
Many thanks in advance,
Michael.


EDIT: Incidentally, if possible the keysym value for the negation key (next to the number 1 on most keyboards when shift is used) would also be appreciated, although not so important as most IDE's use ! instead to represent logical NOT.

---

