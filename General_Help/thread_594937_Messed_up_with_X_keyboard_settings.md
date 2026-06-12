---
title: "Messed up with X keyboard settings"
date: 2007-10-28
forum: General Help
---

### Post by huckey on 2007-10-28
Hi all,
  I am a newbie to Linux world. I was using Ubuntu 7.04 and there I managed somehow to configure my keyboard to allow me entering characters comming from various alphabets: I am using Polish as default but was able to map the "Q" character to enter the "adiaeresis" when depressed with Right Alt. 

  When I upgraded to Ubuntu 7.10 these settings were gone so I decided to try to get it working again. I went into /etc/X11/xkb/symbols/pl (that's my default keyboard layout) and edited it to add the additional mapping. I must have done something wrong though but I can not sort it out.

  In my xorg.conf I have
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "pl"
    Option         "XkbVariant" "basic"

```

  When I log into Ubuntu I get a message saying something about XKB configuration activation error (I get the message in Polish). The message says it can result from many differnt reasons but advises to add xprop -root | grep XKB and gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd) if reporting this error. The output of those commands is:
```

xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "pl", "basic", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "pl", "basic", ""

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = 
 options = [lv3 lv3:ralt_switch]
 overrideSettings = true

```

The contents of my pl file are:
```

// $XKeyboardConfig: xkbdesc/symbols/pl,v 1.10 2006/07/30 19:28:56 svu Exp $

// based on a keyboard map from an 'xkb/symbols/pl' file
//
// $XFree86: xc/programs/xkbcomp/symbols/pl,v 1.3 2003/04/19 12:22:12 pascal Exp $

partial default alphanumeric_keys
xkb_symbols "basic" {

    include "latin"

    name[Group1]="Poland";

    key <AD01>	{ [         q,          Q,   adiaeresis,   Adiaeresis ]	};
    key <AD02>	{ [         w,          W,        aring,        Aring ]	};
    key <AD03>	{ [         e,          E,      eogonek,      Eogonek ]	};
    key <AD08>	{ [         i,          I,   odiaeresis,   Odiaeresis ]	};
    key <AD09>	{ [         o,          O,       oacute,       Oacute ]	};

    key <AC01>	{ [         a,          A,      aogonek,      Aogonek ]	};
    key <AC02>	{ [         s,          S,       sacute,       Sacute ]	};

    key <AB01>	{ [         z,          Z,    zabovedot,    Zabovedot ]	};
    key <AB02>	{ [         x,          X,       zacute,       Zacute ]	};
    key <AB03>	{ [         c,          C,       cacute,       Cacute ]	};
    key <AB06>	{ [         n,          N,       nacute,       Nacute ]	};

    include "keypad(comma)"

    include "level3(ralt_switch)"
};

partial alphanumeric_keys
xkb_symbols "qwertz" {

    // Describes the differences between a very simple en_US
    // keyboard and a very simple QWERTZ Polish keybaord

    include "latin(type3)"

    name[Group1]="Poland - qwertz";

    key <AE01>	{ [         1,     exclam,   asciitilde,   exclamdown ]	};
    key <AE02>	{ [         2,   quotedbl,   dead_caron,    oneeighth ]	};
    key <AE03>	{ [         3, numbersign, dead_circumflex,  sterling ]	};
    key <AE04>	{ [         4,     dollar,   dead_breve,       dollar ]	};
    key <AE05>	{ [         5,    percent,       degree, threeeighths ]	};
    key <AE06>	{ [         6,  ampersand,  dead_ogonek,  fiveeighths ]	};
    key <AE07>	{ [         7,      slash,   dead_grave, seveneighths ]	};
    key <AE08>	{ [         8,  parenleft, dead_abovedot,   trademark ]	};
    key <AE09>	{ [         9, parenright,   dead_acute,    plusminus ]	};
    key <AE10>	{ [         0,      equal, dead_doubleacute,   degree ]	};
    key <AE11>	{ [      plus,   question, dead_diaeresis, questiondown ] };
    key <AE12>	{ [apostrophe,   asterisk, dead_cedilla,  dead_ogonek ]	};

    key <AD03>	{ [         e,          E,     EuroSign,         cent ]	};
    key <AD11>	{ [ zabovedot,     nacute,     division, dead_abovering ] };
    key <AD12>	{ [    sacute,     cacute,     multiply,  dead_macron ]	};

    key <AC02>	{ [         s,          S,      dstroke,      section ]	};
    key <AC03>	{ [         d,          D,      Dstroke,          ETH ]	};
    key <AC08>	{ [         k,          K,          kra,    ampersand ]	};
    key <AC09>	{ [         l,          L,      lstroke,      Lstroke ]	};
    key <AC10>	{ [   lstroke,    Lstroke,       dollar, dead_doubleacute ] };
    key <AC11>	{ [   aogonek,    eogonek,       ssharp,   dead_caron ]	};
    key <TLDE>	{ [  abovedot, dead_ogonek,     notsign,      notsign ]	};

    key <BKSL>	{ [    oacute,     zacute,   dead_grave,   dead_breve ]	};
    key <AB03>	{ [         c,          C,         cent,    copyright ]	};
    key <AB10>  { [     minus, underscore, dead_belowdot, dead_abovedot ] };

    include "keypad(comma)"

    include "level3(ralt_switch)"
};

// Polish Dvorak keymaps
// by Rafal Rzepecki <divide@users.sf.net>

// The base keymap "pl" places Polish quotes on quotemark key and 
// moves the dead symbols from there to "1/!" key. If you are used to common 
// dead keys placement, you could use "pl_altquotes"; in this layout 
// dead keys remain in the old place, whereas Polish quotes are placed on the
// "1/!" key. If you do not use Polish quotes at all, you can use "pl_basic" map.

// Basic Polish keymap (without Polish quotes)
partial alphanumeric_keys 
xkb_symbols "dvorak" {
    include "us(dvorak)"
    
    name[Group1] = "Poland - Dvorak";

    key <AD08> { [	    c,	C,	cacute,	Cacute		]	};
    key <AD10> { [	    l,	L,     lstroke, Lstroke		]	};
    key <AC01> { [	    a,	A,     aogonek, Aogonek		]	};
    key <AC02> { [	    o,	O,      oacute, Oacute		]	};
    key <AC03> { [	    e,	E,     eogonek, Eogonek		]	};
    key <AC09> { [	    n,	N,      nacute, Nacute		]	};
    key <AC10> { [	    s,	S,      sacute, Sacute		]	};
    key <AB09> { [	    v,	V,      zacute, Zacute		]	};
    key <AB10> { [	    z,	Z,   zabovedot, Zabovedot	]	};
    
    include "keypad(comma)"

    // this to allow writing ALL CAPS with a Shift key
    include "level3(ralt_switch)"

    // use one of compose:* options to choose Multi_key, if you will,
    // or layout +level3(ralt_switch_multikey) to revert standard behaviour
};

// Default Polish keymap with Polish quotes on quotemark key
partial alphanumeric_keys
xkb_symbols "dvorak_quotes" {
    include "pl(dvorak)"
    
    name[Group1] = "Poland - Dvorak, Polish quotes on quotemark key";

    key <AD01> { [  apostrophe,	quotedbl, doublelowquotemark, rightdoublequotemark	] };

    // Dead symbols moved to this key
    key <AE01> { [	    1,	exclam, dead_acute, dead_diaeresis 		]	};ubuntu keyboard
};

// Polish keymap with Polish quotes on key "1/!"
partial alphanumeric_keys
xkb_symbols "dvorak_altquotes" {
    include "pl(dvorak)"

    name[Group1] = "Poland - Dvorak, Polish quotes on key 1/!";

    key <AE01> { [	    1,	exclam, doublelowquotemark, rightdoublequotemark	]	};
};

partial alphanumeric_keys
xkb_symbols "csb" {

    include "latin"

    name[Group1]="Poland - Kashubian";

    key <AD03>	{ [         e,          E,      eacute,      Eacute ]	};
    key <AD04>	{ [         r,           R,      ediaeresis,      Ediaeresis ]	};
    key <AD06>      { [         y,          Y,      EuroSign,         cent ]        };
    key <AD07>	{ [          u,          U,       ugrave,       Ugrave ]	};
    key <AD08>	{ [         i,            I,       ograve,       Ograve ]	};
    key <AD09>	{ [         o,          O,       oacute,       Oacute ]	};
    key <AD10>	{ [         p,          P,       ocircumflex,       Ocircumflex ]	};

    key <AC01>	{ [         a,          A,      aogonek,      Aogonek ]	};
    key <AC02>	{ [         s,          S,      atilde,      Atilde ]	      };
    key <AC09>	{ [         l,          L,      lstroke,      Lstroke ]      };

    key <AB01>	{ [         z,          Z,    zabovedot,    Zabovedot ]	};
    key <AB06>	{ [         n,          N,       nacute,       Nacute ]	};

    include "keypad(comma)"

    include "level3(ralt_switch)"
};

```

  Now the error described above appears when loggin into the system and when changing 3rd level choosers on layout options tab in System->Preferences->Keyboard.

  Since this used to work before I must be making some silly mistake now but I can not find it. Can you help?

  Thanks!

Best regards

Huckey

---

