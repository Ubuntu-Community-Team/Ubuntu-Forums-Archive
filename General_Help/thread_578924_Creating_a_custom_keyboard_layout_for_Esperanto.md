---
title: "Creating a custom keyboard layout for Esperanto"
date: 2007-10-17
forum: General Help
---

### Post by kinghajj on 2007-10-17
I want to create an "Esperanto--Dvorak" layout. This layout will not actually be a true Dvorak keyboard for Esperanto, but rather a US Dvorak keyboard with characters like X, Y, W, Q, etc., replaced by the special Esperanto characters.

Here is my current layout file.
```

partial alphanumeric_keys
xkb_symbols "epo-dvorak" {

name[Group1]= "Esperanto - Dvorak";

// Alphanumeric section

key <TLDE> { [       hcircumflex, Hcircumflex	] };

key <AE01> { [	    1,	exclam 		]	};
key <AE02> { [	    2,	at		]	};
key <AE03> { [	    3,	numbersign	]	};
key <AE04> { [	    4,	dollar		]	};
key <AE05> { [	    5,	percent		]	};
key <AE06> { [	    6,	asciicircum, dead_circumflex, dead_circumflex ]	};
key <AE07> { [	    7,	ampersand	]	};
key <AE08> { [	    8,	asterisk	]	};
key <AE09> { [	    9,	parenleft,  dead_grave]	};
key <AE10> { [	    0,	parenright	]	};
key <AE11> { [ bracketleft,	braceleft	]	};
key <AE12> { [ bracketright, braceright,  dead_tilde] };

key <AD01> { [  apostrophe,	quotedbl, dead_acute, dead_diaeresis	] };
key <AD02> { [	comma,	less,   dead_cedilla, dead_caron	] };
key <AD03> { [      period,	greater, dead_abovedot, periodcentered	] };
key <AD04> { [	    p,	P		]	};
key <AD05> { [	    gcircumflex,	Gcircumflex		]	};
key <AD06> { [	    f,	F		]	};
key <AD07> { [	    g,	G		]	};
key <AD08> { [	    c,	C		]	};
key <AD09> { [	    r,	R		]	};
key <AD10> { [	    l,	L		]	};
key <AD11> { [	slash,	question	]	};
key <AD12> { [	equal,	plus		]	};

key <AC01> { [	    a,	A 		]	};
key <AC02> { [	    o,	O		]	};
key <AC03> { [	    e,	E		]	};
key <AC04> { [	    u,	U		]	};
key <AC05> { [	    i,	I		]	};
key <AC06> { [	    d,	D		]	};
key <AC07> { [	    h,	H		]	};
key <AC08> { [	    t,	T		]	};
key <AC09> { [	    n,	N		]	};
key <AC10> { [	    s,	S		]	};
key <AC11> { [	ubreve,	Ubreve	]	};

key <AB01> { [   semicolon,	colon, dead_ogonek, dead_doubleacute ] };
key <AB02> { [	    ccircumflex,	Ccircumflex		]	};
key <AB03> { [	    j,	J		]	};
key <AB04> { [	    k,	K		]	};
key <AB05> { [	    scircumflex,	Scircumflex		]	};
key <AB06> { [	    b,	B		]	};
key <AB07> { [	    m,	M		]	};
key <AB08> { [	    jcircumflex,	Jcircumflex		]	};
key <AB09> { [	    v,	V		]	};
key <AB10> { [	    z,	Z		]	};
};

```

The problem is that there is not enough space! As you can see, the "-" key is replaced by a "u-breve", and the "~" in replaced by a "hcircumflex".

So, I'm wondering if there is a way to configure the layout so that when one keypress follows another--say, "u" follows "a"--that, instead of the normal "u", a "u-breve" appears.

Also, is there a way to configure the layout so that when I press, say, Ctrl+Alt+Super+H, that the "hcircumflex" character appears? I really would like to get the tilde back.

Thanks in advance to all who help!

---

