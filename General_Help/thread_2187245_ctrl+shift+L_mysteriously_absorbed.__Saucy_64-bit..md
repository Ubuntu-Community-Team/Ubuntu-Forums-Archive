---
title: "ctrl+shift+L mysteriously absorbed.  Saucy 64-bit."
date: 2013-11-11
forum: General Help
---

### Post by rickyseltzer on 2013-11-11
Something is absorbing ctrl+shift+L.  Can you help me find what?
I've looked in all the obvious configuration screens in settings and in the tweaks programs.
In sublime-text, the key simply does not appear when I ask it to display keystrokes.  All the other keystrokes display fine.
In terminator, ctrl+shift+L flashes the top bar (containing the current directory and the character dimensions of the screen).

Xev shows** different kinds of output** from ctrl+shift+K and ctrl+shift+L:

_First [FONT=arial]Ctrl+Shift+[/FONT]K, key-up and key-down:_[INDENT][FONT=courier new]KeyPress event, serial 28, synthetic NO, window 0x6800001,
    root 0x91, subw 0x0, time 20311193, (146,80), root:(1507,132),
    state 0x15, keycode 45 (keysym 0x4b, K), same_screen YES,
    XLookupString gives 1 bytes: (0b) "
                                       "
    XmbLookupString gives 1 bytes: (0b) "
                                         "
    XFilterEvent returns: False

KeyRelease event, serial 28, synthetic NO, window 0x6800001,
    root 0x91, subw 0x0, time 20311305, (146,80), root:(1507,132),
    state 0x15, keycode 45 (keysym 0x4b, K), same_screen YES,
    XLookupString gives 1 bytes: (0b) "
                                       "
    XFilterEvent returns: False
[/FONT][/INDENT]
[FONT=arial]
_Now Ctrl+Shift+L, key-up and key-down are only one event! _[/FONT][INDENT][FONT=courier new]KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  4294967185 0   0   0   32  0   4   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

[/FONT][/INDENT]
Any help would be appreciated.  I guess I have configured something wrong.
~/.Xmodmap has only a pointer line, for scrolling.

---

### Post by Frogs Hair on 2013-11-11
> [COLOR=#000000]Something is absorbing ctrl+shift+L[/COLOR] Can you please explain  what is meant by this . I don't see that key binding associated with any actions in key board settings, but the action may be disabled on my system. What action and in what program is the key-binding used ?

---

### Post by rickyseltzer on 2013-11-11
It's a command in the text editor sublime-text.  It modifies the scope of selected text.  But it doesn't work. 
I started tracking this down on the forum for the sublime-text editor.  There's a diagnostic command to display all keystrokes.
ctrl-shift-K appears but ctrl-shift-L does not.  So I tried those keystrokes outside of the editor in xev and got the strange results above.

---

### Post by Frogs Hair on 2013-11-11
If it is the program at the link I see that is not available in the software-center and don't know about compatibility with 13.10 . I download and started the unregistered  version of Sublime Text 2 and don't get any action from the  key-binding  inside or outside of the program

 [http://www.sublimetext.com/](http://www.sublimetext.com/)

---

### Post by rickyseltzer on 2013-11-11
Make a 5-line text selection and hit ctrl shift L, it's supposed to change to multiple selections.  That is, replacing 5 lines of text with the letter 'a' would result in 4 lines deleted and one 'a'.  But if you do ctrl shift L first, then each of the 5 lines is replaced by an 'a', resulting in 5 lines with only 'a'.

The doc on what the keystrokes are supposed to do is here:[ ]("http://http://docs.sublimetext.info/en/latest/editing/editing.html#transforming-multiple-selections-into-lines")[http://docs.sublimetext.info/en/latest/editing/editing.html#transforming-multiple-selections-into-lines](http://docs.sublimetext.info/en/latest/editing/editing.html#transforming-multiple-selections-into-lines)
The sublime-text support forum discussion is here: [http://www.sublimetext.com/forum/viewtopic.php?f=3&t=14595](http://www.sublimetext.com/forum/viewtopic.php?f=3&t=14595)

---

### Post by rickyseltzer on 2013-11-11
Also, on my system, when in Terminator (Terminal) I type ^V Ctrl-Shift-K, I see the ^K,   But if I type ^V Ctrl-Shift-L, it does not appear.

---

