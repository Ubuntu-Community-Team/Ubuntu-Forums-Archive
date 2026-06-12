---
title: "How to make a custom keyboard layout?"
date: 2013-12-11
forum: General Help
---

### Post by dorigoluca on 2013-12-11
Hi, maybe this was asked before but I don't really know what to search for...

So here is my problem: both of my shift keys are dead and I need to assign the "shift" function to an other key in order to capitalize things etc. 

I already did some research and found ways to change the layout for the normal keys (letters numbers and symbols) but not for shift, alt, etc. :(

Is there a graphical utility to do this? Otherwise please be gentle on the explanation, I am quite new to that Terminal thing :-p

tyvm!!!

luca

---

### Post by Impavidus on 2013-12-11
Use xmodmap.

It's some time since I last did this, but I think you can use xev to find the key code of the key you want to use as shift. Type **xev** in a terminal and hit enter. You'll get a small window. Hit the key you want to use as shift key and note the key code. For example, when I try the right alt key I get```
KeyPress event, serial 34, synthetic NO, window 0x5000001,
    root 0xae, subw 0x0, time 4630700, (-5,67), root:(588,372),
    state 0x10, keycode **108** (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x5000001,
    root 0xae, subw 0x0, time 4630751, (-5,67), root:(588,372),
    state 0x18, keycode **108** (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```indicating this key has code 108.

Next create a file with the modifications you want. For example, if you want to map key 108 to the right shift key, put in your file```
keycode 108 = Shift_R
```The left shift key is of course Shift_L, but most applications don't care which shift key you use. Save the file as **.xmodmap** in your home directory (although I don't think it really matters how you call the file). To activate the change run the command ```
xmodmap ~/.xmodmap
``` in a login script.

---

### Post by dorigoluca on 2013-12-11
Thanks for your answer!

Ok so I created a file with gedit with "keycode 135 = Shift_R" (normally it is the "menu" key) and placed it in the home folder with the name ".xmodmap".

then I went to "startup applications" and added a command saying "xmodmap ~/.xmodmap".

It worked it some point because when I run "xmodmap" I get "keycode 135 = Shift_R NoSymbol Shift_R" but when I press the key along with a letter, it doesn't seem to do its "shift" job :'( (the letter is not capitalised)
 

any idea?

---

### Post by dorigoluca on 2013-12-11
I managed to do it thanks to this [http://offend.me.uk/blog/14/](http://offend.me.uk/blog/14/) , thanks a lot anyway!!

---

