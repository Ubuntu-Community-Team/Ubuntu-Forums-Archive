---
title: "Custom keyboard stops working in Xenial"
date: 2016-05-15
forum: General Help
---

### Post by macho3 on 2016-05-15
My   custom keyboard layout stopped working under Xenial. Five years ago I added 3rd- and 4th-level multilingual keys to a basic Dvorak layout.  I can still choose this custom layout, but it now only includes basic Dvorak keys, without my additions.

Thanks for any suggestions you can provide.

To add this layout, the edits I made are as follows:

**added a line for the layout to /usr/share/X11/xkb/rules/evdev.lst**:
```
  multi-dvorak    ca: Custom Canadian Multilingual Dvorak
```

** added a section for the layout to /usr/share/X11/xkb/rules/evdev.xml:**
```
        <variant>
          <configItem>
            <name>multi-dvorak</name>
            <shortDescription>dv</shortDescription>
            <description>Canadian Multilingual (Dvorak)</description>
          </configItem>
        </variant>

```

**added a they keys for the layout to /usr/share/X11/xkb/symbols/ca:**
```
partial
xkb_symbols "multi-dvorak" {

    name[Group1] = "Canadian Multilingual (Dvorak)";

// Alphanumeric section
    key <TLDE> { [       grave, asciitilde, dead_grave, dead_tilde  ] };

    key <AE01> { [      1,  exclam, onesuperior, exclamdown     ] };
    key <AE02> { [      2,  at, twosuperior, onehalf    ] };
    key <AE03> { [      3,  numbersign, onethird, threequarters ] };
    key <AE04> { [      4,  dollar, onequarter, EuroSign    ] };
    key <AE05> { [      5,  percent, twothirds    ] };
    key <AE06> { [      6,  asciicircum, acircumflex, dead_circumflex ] };
    key <AE07> { [      7,  ampersand ] };
    key <AE08> { [      8,  asterisk, oneeighth, multiply ] };
    key <AE09> { [      9,  parenleft,  dead_grave] };
    key <AE10> { [      0,  parenright, degree  ] };
    key <AE11> { [ bracketleft, braceleft ] };
    key <AE12> { [ bracketright, braceright,  dead_tilde] };

    key <AD01> { [  apostrophe, quotedbl, dead_acute, dead_diaeresis  ] };
    key <AD02> { [  comma,  less,   dead_cedilla, guillemotleft ] };
    key <AD03> { [      period, greater, ellipsis, guillemotright ] };
    key <AD04> { [      p,  P, paragraph, lessthanequal   ] };
    key <AD05> { [      y,  Y, greaterthanequal, greaterthanequal   ] };
    key <AD06> { [      f,  F, epsilon   ] };
    key <AD07> { [      g,  G, lambda   ] };
    key <AD08> { [      c,  C, ccedilla, Ccedilla   ] };
    key <AD09> { [      r,  R   ] };
    key <AD10> { [      l,  L, sterling, yen    ] };
    key <AD11> { [  slash,  question, exclamdown, questiondown  ] };
    key <AD12> { [  equal,  plus, notequal, plusminus   ] };

    key <AC01> { [      a,  A, agrave, Agrave     ] };
    key <AC02> { [      o,  O, egrave, Egrave ] };
    key <AC03> { [      e,  E, eacute, Eacute   ] };
    key <AC04> { [      u,  U, ugrave, Ugrave   ] };
    key <AC05> { [      i,  I   ] };
    key <AC06> { [      d,  D   ] };
    key <AC07> { [      h,  H   ] };
    key <AC08> { [      t,  T, registered, copyright    ] };
    key <AC09> { [      n,  N   ] };
    key <AC10> { [      s,  S, section    ] };
    key <AC11> { [  minus,  underscore, emdash, endash  ] };

    key <AB01> { [   semicolon, colon, leftsinglequotemark, leftdoublequotemark ] };
    key <AB02> { [      q,  Q, rightsinglequotemark, rightdoublequotemark   ] };
    key <AB03> { [      j,  J   ] };
    key <AB04> { [      k,  K   ] };
    key <AB05> { [      x,  X   ] };
    key <AB06> { [      b,  B   ] };
    key <AB07> { [      m,  M, mu   ] };
    key <AB08> { [      w,  W, ae, AE   ] };
    key <AB09> { [      v,  V, oe, OE   ] };
    key <AB10> { [      z,  Z, notsign    ] };

    key <BKSL> { [  backslash,  bar, egrave, Egrave             ]       };

    key <SPCE> { [ space, space, nobreakspace, nnbrspace ] };
};
```

---

