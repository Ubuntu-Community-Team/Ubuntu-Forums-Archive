---
title: "Mapping unused key as Super-key"
date: 2014-07-26
forum: General Help
---

### Post by foberle on 2014-07-26
I'm using a "real" keyboard from a few decades ago (a Northgate Omnikey Ultra) that has served me well through many PCs over the years but, as with all keyboards of that generation, it has no "super" ("Windows") key. It has an unused key that I would like to remap to serve as a "Super" Key, but none of the documentation I've located seems to apply to Ubuntu 14.04; indeed most of it refers to locations and utilities that don't exist in Ubuntu 14.04.

The key in question produces a keycode of 120 according to the following xev output:

KeyPress event, serial 37, synthetic NO, window 0x4000001,
    root 0x2c5, subw 0x0, time 48472296, (-32,-123), root:(859,363),
    state 0x10, keycode 120 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4000001,
    root 0x2c5, subw 0x0, time 48472382, (-32,-123), root:(859,363),
    state 0x10, keycode 120 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

So I added and commented out lines in /usr/share/X11/xkb/keycodes/xfree86 as below:
    // Microsoft keyboard extra keys
// Comment and addition on 2014-07-25 to use unused physical Omni Key as a replacement for the Windows Key
//    <LWIN> = 115;
    <LWIN> = 120;
. . .
// Commented out on 2014-07-25 to use actual Omni Key as a Windows Key
//    <FK15> =  120;

After rebooting, the key is recognized as "Super_L" as shown in the xev output below:

KeyPress event, serial 37, synthetic NO, window 0x4200001,
    root 0x2c5, subw 0x0, time 49142127, (241,-71), root:(1132,415),
    state 0x10, keycode 120 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
    root 0x2c5, subw 0x0, time 49142270, (241,-71), root:(1132,415),
    state 0x50, keycode 120 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

I assume from this that I chose the correct file to edit from the usr/share/X11/xkb/keycodes directory (how, by the way, would I have been able to determine which file was loaded/used when 14.04 starts? - I just pciked that as most likely by browsing through the many available.).
Pressing the key, however, does absolutely nothing. The Keyboard facility in System Settings seems to offer no method for assigning keys - only for assigning functions to existing keys.

Running "xmodmap -pm" gives the following output:

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x78),  Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

Does this mean that the "Super_L" key is only a modifier? What I want is the stock functionality of the key. Should I comment out or remove the mod4 line?

The key I'm attempting to map, by the way, is labelled "Omni" and is located in the center of a separate grouping (not the "numeric keypad") laid out like this, and with the keycodes reported by xev:
 ________________________________________
| Home       |   Up Arrow  |   PageUp    |
|    110     |     111     |    112      |
|----------------------------------------|
| Left Arrow |   OmniKey   | Right Arrow |
|    113     |     120     |    114      |
|----------------------------------------|
| End        |  Down Arrow |  PageDown   |
|    115     |     116     |    117      |
|----------------------------------------|
|       Insert      |        Delete      |
|        118        |         119        |
 ----------------------------------------

I looked under /usr/share/X11/xkb/symbols to see if there was a corresponding xfree86 mapping, but there was none, so the "us" mapping seems to be the one in use. The Home, Arrow and Page Up/Down keys work as expected, although they have different keycodes than the ones on the numeric keypad. I am guessing that adding a line to the "us" file such as:

    key <LWIN> {  [  ??, ??, ??, ??  ]  };

might do the trick, but what would I enter in place of the ?? characters (i.e. where are the definitions of values such as "minus" "underscore" and such, or what would it be for windows key functionality?

Since the Ubuntu System Settings didn't provide anything useful for addressing this, I followed another recommendation to use something called "gnome-control-center' from the command line. Ubuntu helpfully informed me that this was not available on my system, but could be installed by typing "sudo apt-get install gnome-control-center". So I did that, and it went through the usual process, after which I was able to launch this from the command line.

Surprise, surprise. Gnome Control Center is, in fact, the utility presented by the Systems Setting choice on the main screen. Of course, now I'm terrified that if I "uninstall" it (as it's obviously the same thing and therefore redundant) some things will be inadvertantly removed.

I've run dconf-editor, and found the following sections (recommended by a few folks), but these all just seem to duplicate the entries in the GUI tools, and have no apparent way to tell the system that my Omni key is really a "Super" key:
   org | onboard | keyboard section
   org | gnome | desktop | wm | keybindings 
   org | gnome | libgnomekbd | settings-daemon | peripherals | keyboard

Can anyone tell me what I'm missing?

---

### Post by coldcritter64 on 2014-07-26
You could consider trying this in software with xdotool. Install xdotool from the repos. Go to System Settings > Keyboard > Keyboard Shortcuts. Set up a custom shortcut mapping the "spare" key to the command ...

```
xdotool key "Super"
```

Then when you press your spare key the custom shortcut activates the xdotool command which imitates a key press at the software level. I'm not sure about your keyboard but this may be a workaround that could work out for you.

Edit: I haven't tried out 14.04 yet. I am assuming the custom keyboard shortcuts are still available as they were in older versions (12.04).

---

### Post by foberle on 2014-07-26
Thanks much for the reply.

In the words of the Ubuntu help page,  xdotool requires "any valid X Keysym string" (such as the Super_L I'm  trying to assign my key to), so this won't work, since it must already  be defined somewhere else. In other words, if I can't refer to the key I  want to assign with xdotool and, even if I could, Super_L doesn't yet  exist.

My memory might be faulty or confused with another machine, but it seems to me that the custom keyboard shortcuts were more comprehensive in 12.)4 than they are with 14.04...

But Thanks.

---

