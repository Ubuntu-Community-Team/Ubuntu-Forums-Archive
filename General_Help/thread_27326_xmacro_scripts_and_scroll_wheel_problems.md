---
title: "xmacro scripts and scroll wheel problems"
date: 2005-04-15
forum: General Help
---

### Post by wondering_jew on 2005-04-15
I have been struggling with getting my keyboard working properly, I read the howto on multimedia keyboards and googled all over the place and can't find anything that will tell me:

1) Where to/how to make a script for the xmacro utility... i can find sample scripts and references to these scripts all over the place but the documentation avaliable seems to presuspose you know where to and how to make it in the first place; 
2) How to get the scroll wheel on the keyboard to function. I assigned the scroll wheel key codes and xev reconizes that something is happening which is better than i had before my output looks like this:

When I scroll down
"KeyRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x8e, subw 0x0, time 51431886, (271,241), root: (277,293),
    state 0x10, keycode 197 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:"

When I scroll up
"KeyPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x8e, subw 0x0, time 51490608, (346,412), root: (352,464),
    state 0x110, keycode 197 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False"

It seems that xev reconizes the scroll wheel as one event where up is the press and down is the release. Looking at avaliable keysyms I found there are keysyms called XF86ScrollUp and XF86ScrollDown and I'm thinking these will have something to do with the problem. Any help would be appreciated I've been trying to figure it out for months.

I should add that my keyboard is not supported by gnome nor hotkeys

---

