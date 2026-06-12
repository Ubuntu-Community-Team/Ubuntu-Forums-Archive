---
title: "the &quot;backslash/vertical line&quot; key on keyboard works like the &quot;dot&quot; key"
date: 2014-12-14
forum: General Help
---

### Post by Vincent_LI on 2014-12-14
I got a new ubantu laptop recently. What bugs me is the the "backslash/vertical line" key , which is above "enter" key works like the "dot" key. I have tried to modify keyboard layout but it does not work. (I get this laptop right here in the US from system76 and I set up keyboard layout as standard USA version, which does not help). I have checked a lot of posts online, but mainly talking about changing keyboard layout, which does not help.

Any idea will be appreciated.

---

### Post by carl4926 on 2014-12-14
The location of the key you describe will be located differently for others, for me it's next to Z and SHIFT on the left sector of this small form factor ASUS netbook
But
\ |
It works fine

Your question is confusing, at least to me. And reads like this key is producing a dot ( . ) as opposed to \ |

Try selecting the keyboard language from the top panel, where the battery power indicator and volume etc... are
And try again

---

### Post by Bashing-om on 2014-12-14
Vincent_LI; Hello;

In addition to carl4926'a advise, what does the tool 'xev' report for the keycode recognized ?
```

xev

```
On my system US querty keyboard :
```

KeyPress event, serial 37, synthetic NO, window 0x2c00001,
    root 0x277, subw 0x2c00002, time 3604479, (49,41), root:(760,417),
    state 0x0, keycode 51 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XmbLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x2c00001,
    root 0x277, subw 0x2c00002, time 3604589, (49,41), root:(760,417),
    state 0x0, keycode 51 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x2c00001,
    root 0x277, subw 0x2c00002, time 3650358, (49,41), root:(760,417),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x2c00001,
    root 0x277, subw 0x2c00002, time 3652358, (49,41), root:(760,417),
    state 0x1, keycode 51 (keysym 0x7c, bar), same_screen YES,
    XLookupString gives 1 bytes: (7c) "|"
    XmbLookupString gives 1 bytes: (7c) "|"
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x2c00001,
    root 0x277, subw 0x2c00002, time 3652467, (49,41), root:(760,417),
    state 0x1, keycode 51 (keysym 0x7c, bar), same_screen YES,
    XLookupString gives 1 bytes: (7c) "|"
    XFilterEvent returns: False

```

Maybe do some remapping of the key ?

[INDENT][INDENT]a failure to communicate ?
[/INDENT][/INDENT]

---

### Post by mc4man on 2014-12-14
When you received this laptop did the \ work?
If not then call system76
If it did & now doesn't then maybe something you did. What happens in a guest session?

---

### Post by Enjabain on 2014-12-19
I have the exact same issue with my system 76 laptop, though i bought mine 6 months ago. let me know if you find a solution.

---

### Post by Enjabain on 2014-12-19
So i just found a solution. from this article:     
[http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys-or-devices](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys-or-devices)

The gist is to type "xev" into terminal. Then press the trouble key. It will tell you the keycode for the eroneous key. Mine was 129. 
Then in a new terminal type:
> xmodmap -e "keycode 129 = backslash bar"
This should make your key work like it is supposed to. But it will not save the changes.
To make the change permanent type:
> xmodmap -pke >~/.Xmodmap
  (it creates a file named .Xmodmap in your home directory (~))
  Then you have to create a file named **.xinitrc** in your home directory where you put command xmodmap .Xmodmap in.


EDIT: Later versions of ubuntu will not run .Xmodmap on startup. To solve this is simply added this as a startup application command.
> xmodmap -e "keycode 129 = backslash bar"


I also put in a ticket with System 76, so it will be interesting to see what they say.
Good luck!

---

