---
title: "Keyboard remapping?"
date: 2008-05-08
forum: General Help
---

### Post by volksstimme on 2008-05-08
Hey guys.

I was wondering, is it possible to remap the keys in Ubuntu?

I'm often writing in German as well as English, and I find it much easier if I have (quick) access to the umlaute characters as well as the eszett (ß). 
Admittedly, Alt Gr + s does make an eszett, but I'd much rather have (left) alt + s, as well as alt + a, alt + o, alt + u, alt + shift + a, etc, etc...

I surely can't be the only person wanting this? I've seen some of the most remote things, but I can't find anything for this (what I'd've thought to be quite common) problem...

Any help is appreciated. =]

---

### Post by volksstimme on 2008-05-18
Bumping this up again.

Learnt a bit more since last time, but still can't do it.
xev won't give the character code for Alt + s, since it's two different keys, it just gives alt and then s, which means I therefore can't use xmodmap.

This should surely be quite simple...

---

### Post by volksstimme on 2008-05-18
Bbbbbump.

---

### Post by volksstimme on 2008-05-18
Ok, I've now got the hang of Compose key (using rwin), but it's still a bit slow/will take a bit of getting used to.
Does nobody have anything?

And how can I set my own Compose Key sequences?

---

### Post by volksstimme on 2008-06-01
Ok guys, I sorted it, pretty much.
This is for anyone curious but who still can't find the method.


Using several sites, I dove in at the deep end and edited the **/usr/share/X11/xkb/symbols/gb** file (depending on your keyboard layout, gb, us, etc.)

This is my current gb file:
```
// $XKeyboardConfig: xkeyboard-config/symbols/gb,v 1.11 2006-10-03 22:25:41 svu Exp $

// based on a keyboard map from an 'xkb/symbols/gb' file
//
// $XFree86: xc/programs/xkbcomp/symbols/gb,v 1.6 2003/10/04 10:25:14 pascal Exp $

partial default alphanumeric_keys
xkb_symbols "basic" {

    // Describes the differences between a very simple en_US
    // keyboard and a very simple U.K. keyboard layout defined by
    // the SVR4 European Language Supplement and sometimes also
    // known as the IBM 166 layout.

    include "latin"

    name[Group1]="United Kingdom";

    key <AE02>	{ [         2,   quotedbl,  twosuperior,    oneeighth ]	};
    key <AE03>	{ [         3,   sterling, threesuperior,    sterling ]	};
    key <AE04>	{ [         4,     dollar,     EuroSign,   onequarter ]	};

    key <AC11>	{ [apostrophe,         at, dead_circumflex, dead_caron]	};
    key <TLDE>	{ [     grave,    notsign,          bar,          bar ]	};

    key <BKSL>	{ [numbersign, asciitilde,   dead_grave,   dead_breve ]	};
    key <LSGT>	{ [ backslash,        bar,          bar,    brokenbar ]	};
    key <AD07>	{ [  u,		U	, udiaeresis, Udiaeresis ] };
    key <AD09>	{ [  o,		O	, odiaeresis, Odiaeresis ] };
    key <AC01>	{ [  a,		A	, adiaeresis, Adiaeresis ] };
    key <AC02>	{ [  s,		S	, ssharp ]	};

    include "level3(ralt_switch_multikey)"
};

partial alphanumeric_keys 
xkb_symbols "intl" { 

    // Describes the differences between a very simple en_US 
    // keyboard and a very simple U.K. keyboard layout with 
    // dead keys. By Phil Jones (philjones1@blueyonder.co.uk) 

    // Includes the following keys: 
    // dead_grave 
    // dead_acute 
    // dead_circumflex 
    // dead_tilde 
    // dead_diaeresis 

    include "latin" 

    name[Group1]="United Kingdom - International (with dead keys)"; 

    key <AE02>  { [   2,  dead_diaeresis,      twosuperior,     onehalf ] };
    key <AE03>  { [   3,        sterling,    threesuperior,    onethird ] };
    key <AE04>  { [   4,          dollar,         EuroSign,  onequarter ] };
    key <AE06>  { [   6, dead_circumflex,         NoSymbol,    onesixth ] };

    key <AC11>  { [ dead_acute,         at,     apostrophe,         bar ] };
    key <TLDE>  { [ dead_grave,    notsign,            bar,         bar ] };

    key <BKSL>  { [ numbersign, dead_tilde,            bar,         bar ] };
    key <LSGT>  { [  backslash,        bar,            bar,         bar ] };

    include "level3(ralt_switch)"
};

// Dvorak (UK) keymap (by odaen) allowing the usage of
// the £ and ? key and swapping the @ and " keys.

partial alphanumeric_keys
xkb_symbols "dvorak" {
    include "us(dvorak)"

    name[Group1]="United Kingdom - Dvorak";

    key <BKSL> { [ numbersign,	asciitilde	] };
    key <AE02> { [	    2,	quotedbl,  twosuperior,   NoSymbol	] };
    key <AE03> { [	    3,	sterling,  threesuperior, NoSymbol	] };
    key <AE04> { [	    4,	dollar,    EuroSign,      NoSymbol	] };
    key <LSGT> { [  backslash,	bar		] };
    key <AD01> { [ apostrophe,	at		] };
};

// Copied from macintosh_vndr/gb
partial alphanumeric_keys 
xkb_symbols "mac" {

    // Describes the differences between a very simple en_US
    // keyboard and a very simple U.K. keyboard layout

    include "latin"

    name[Group1]= "United Kingdom - Macintosh";

    key <AE02> {	[               2,              at,         EuroSign	]	};
    key <AE03> {	[               3,        sterling,       numbersign	]	};

    // End alphanumeric section
    
    include "level3(ralt_switch)"
};


```

**The key part is **

```

    key <AD07>	{ [  u,		U	, udiaeresis, Udiaeresis ] };
    key <AD09>	{ [  o,		O	, odiaeresis, Odiaeresis ] };
    key <AC01>	{ [  a,		A	, adiaeresis, Adiaeresis ] };
    key <AC02>	{ [  s,		S	, ssharp ]	};

```

from the partial default alphanumeric keys section.
The key codes can be retrieved from the **/usr/share/X11/xkb/keycodes/xfree86** file and by using the **xev program**.

Make sure to backup your keyboard config file before editing it.

Now I can just press Right-Alt and u to produce a ü; Right-Alt, Shift and o for a Ö; and so on.

---

### Post by peterroots on 2008-06-05
Thanks for this, got me off to a really good start, but....

I tried this, or something similar, as I have a us keyboard and wanted the pound sign instead of the dollar.  I found that by selecting us intl option I got all sorts of extras, but things like ' " ` ~ became dead keys that added accents over the next letter - handy but not what I wanted and right-alt $ was not how I wanted to get pound.
After editing the /usr/share/X11/xkb/symbols/us file I was able to swap the dead keys and ordinary keys around and swap dollar for pound.
Great!
Then I turned my computer off - bad move!
now I only get the basic us keyboard with none of the changes that worked after my edit.  the edited us file is still as it was but does not work anymore :confused:
Since then I have found that the problem was that the edited file contained a different number of characters to the original - don't know why this is a problem but it is.  After trying again, and taking care not to change the file length, all is now working fine

---

### Post by deltaprime on 2008-06-05
i just use two usb keyboards that i hotswap when i need them... it works way fast er and its easier, es ist einfach viel einfacher ;)

---

### Post by drs305 on 2008-06-05
When I have a single key to program, I do what I wrote about in this post using xmodmap and putting a command in Sessions, Startup:
[http://ubuntuforums.org/showthread.php?t=819249#2]("http://ubuntuforums.org/showthread.php?t=819249#2")

---

