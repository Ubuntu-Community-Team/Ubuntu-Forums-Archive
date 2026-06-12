---
title: "[HELP] Backspace/Keyboard issue: Adds character p instead of deleting characters"
date: 2015-12-23
forum: General Help
---

### Post by Anomime on 2015-12-23
Hi, using Ubuntu 14.04
Here's my issue i have a laptop K450J of Asus and when i push on the button backspace it adds the character p and when i push the character p, nothing happens almost tries to delete but doesn't. 

BTW I write all of this with a usb keyboard instead of the built in on the laptop.

---

### Post by Anomime on 2015-12-23
You can find out what the particular keys are actually doing by opening a terminal and typing

```
xev
```

That brings up a square box named Event Tester.  Put the mouse cursor in there and hit the questionable keys - it will show you what they actually are doing.

The full story is here:

                         [COLOR=#333333][FONT=arial][SIZE=1][[FONT=Liberation Serif][SIZE=3]http://www.linux.com/learn/tutorials/320420-weekend-project-configure-your-keyboard-into-submission[/SIZE][/FONT]]("http://www.linux.com/learn/tutorials/320420-weekend-project-configure-your-keyboard-into-submission")[/SIZE][/FONT][/COLOR]
  


  [COLOR=#333333][FONT=arial][SIZE=1][URL="http://www.linux.com/learn/tutorials/320420-weekend-project-configure-your-keyboard-into-submission"][FONT=Liberation Serif][SIZE=3]

[/SIZE][/FONT][/URL][/SIZE][/FONT][/COLOR]

I noticed on my keyboard settings i put repeat when i press a button but... the problem remains!
Even though it shows it still replaces with p.

```
MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 37, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 5957933, (53,47), root:(53,637),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XmbLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 5957996, (53,47), root:(53,637),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False
```

Ok somehow the backspace is working again but i want to know... Why it did that.

It adds the following: (When i press only backspace) 

```
KeyPress event, serial 39, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 2452776, (30,39), root:(30,91),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XmbLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 2452786, (30,39), root:(30,91),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 2452800, (30,39), root:(30,91),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 2452848, (30,39), root:(30,91),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False
```

It adds the following: (When i only press p)

```
KeyPress event, serial 37, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 3883680, (36,41), root:(36,93),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XmbLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 3883690, (36,41), root:(36,93),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 3883728, (36,41), root:(36,93),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 3883738, (36,41), root:(36,93),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False
```

And when i ran the command: xmodmap -pke
Backspace:

```
keycode  22 = BackSpace BackSpace BackSpace BackSpace
p:
keycode  33 = p P p P thorn THORN
```

It gave me these... how do i know which to change?

---

### Post by egeezer on 2015-12-23
Somewhere along the line the keyboard configuration was set to a different language/keycount/other, I think, since the xmodmap includes the character Thorn.

---

### Post by Anomime on 2015-12-23
What is the character Thorn?

---

### Post by Vladlenin5000 on 2015-12-24
> **Anomime said:**
> What is the character Thorn?

[https://en.wikipedia.org/wiki/Thorn_%28letter%29](https://en.wikipedia.org/wiki/Thorn_%28letter%29)

---

### Post by mörgæs on 2015-12-24
For an Icelander it was a nice little Christmas present to see Þ in the forum. We don't get a lot of that. 

Anyway, back on track and sorry for going off-topic.

---

### Post by Anomime on 2015-12-24
Well the problem is back... And i can't for the life of me figure out. Why am i getting this error? And it's the same... Overnight i got the error...
Maybe egeezer is right
"Somewhere along the line the keyboard configuration was set to a  different language/keycount/other, I think, since the xmodmap includes  the character Thorn."
How do i fix my keyboard layout so it stays the default one... for me it's Portuguese so..

---

### Post by HermanAB on 2015-12-24
You can set the language preference in your desktop system somewhere - different for KDE, Gnome, XFCE etc.

---

### Post by Anomime on 2015-12-24
Still have the same problem.
I hadn't installed my language packs in Language Support but it doesn't work somehow..

Current code on only pressing the Backspace:

```

MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 37, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 652509, (16,14), root:(1011,592),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XmbLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 652521, (16,14), root:(1011,592),
    state 0x0, keycode 112 (keysym 0xff55, Prior), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 652529, (16,14), root:(1011,592),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 652541, (16,14), root:(1011,592),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 652551, (16,14), root:(1011,592),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4000001,
    root 0x9c, subw 0x4000002, time 652564, (16,14), root:(1011,592),
    state 0x0, keycode 112 (keysym 0xff55, Prior), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```
As you can see it presses the p button, Page Up button and Backspace button but i don't know why..

---

### Post by Anomime on 2015-12-25
Now my keyboard layout is all around messed up when i press backspace i can delete but it only deletes and then goes up through the page or goes to the first character on a line. I don't know what to do.

---

