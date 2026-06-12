---
title: "Need xkb help for an 87 key keyboard"
date: 2014-09-21
forum: General Help
---

### Post by CliveMcCarthy on 2014-09-21
I'm grappling with **xkbcomp** and **setxkbmap**. I have editied an **xkb_keycode.xkb** file derived from an **xkbcomp -xkb** output which has all the necessary sections: **keycodes, types, symbols, compatibility & geometry**. I have compiled my edited version (no errors and warning only at level 10) and have run it through **xkbcomp** again to get a **xkm** file.

So far so good.

Then on to **setxkbmap** which is confounding. When I feed it the compiled **xkm** file it uses default/installed values for the subsections instead of those compiled in the **xkm** map file !? So I chopped up the compound xkb file, created a top-level xkb file and 'included' the section files. It seem the output of **xkbcomp -xkb** can't be fed directly into **setxkbmap.** I then spoon fed **setxkbmap** with the source sections but, I suppose it found the **xkm** file anyhow?

```

Clive@Q9550 ~ $ setxkbmap -model pc87 -compat pc87_compatibility -geometry pc87_geometry -symbols pc87_symbols -keycodes pc87_keycodes -types pc87_types -v 10
Setting verbose level to 10
locale is C
Warning! Multiple definitions of keyboard model
         Using command line, ignoring X server
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Warning! Multiple definitions of keycodes
         Using command line, ignoring rules file
Warning! Multiple definitions of symbols
         Using command line, ignoring rules file
Warning! Multiple definitions of types
         Using command line, ignoring rules file
Warning! Multiple definitions of compatibility map
         Using command line, ignoring rules file
Warning! Multiple definitions of geometry
         Using command line, ignoring rules file
Applied rules from evdev:
rules:      evdev
model:      pc87
layout:     us
Trying to build keymap using the following components:
keycodes:   pc87_keycodes
types:      pc87_types
compat:     pc87_compatibility
symbols:    pc87_symbols
geometry:   pc87_geometry
Error loading new keyboard description
```

So there are warnings about multiple definitions and that the "rules" are being ignored so I suspect the "rules" are getting in the way. Chopping up the **xkb** file seems quite unnecessary, particularly for a one-off custom keyboard arrangement. :mad:

Many hours later:
So this command of **xkbcomp** is MUCH cleaner: [FONT=courier new]**sudo xkbcomp pc87_big_keymap.xkb -I :0.0 -v -w 10**[/FONT] and it seems you don't need **setxkbmap** at all! It will compile a keymap, not look anywhere else, and upload it to the display (the X server) .

The thing of particular note is the[FONT=courier new] **-I** [/FONT]option with NO path, is the answer. The creators of xkbcomp decided to mess with the _normal sequence_ of searched directories. The default action is to search the current directory LAST. It isn't bad it just isn't what gcc and other compilers do. Which makes it POSITIVELY WICKED  :twisted:

```
//-----------------------------------------------------------------------------------
//                            These are the new yellow keys
//-----------------------------------------------------------------------------------

    key <PRSC> {[XF86Cut]}; // new cut
    key <SCLK> {[XF86Copy]};  // new copy
    key <PAUS> {[XF86Paste]};  // new paste

//-----------------------------------------------------------------------------------
```

This works! However, only for some applications. I suspect gtk+ filters these. I'm still  hacking around, so any help would be highly appreciated.

BTW does anyone know what xkbwatch is supposed to do?

---

