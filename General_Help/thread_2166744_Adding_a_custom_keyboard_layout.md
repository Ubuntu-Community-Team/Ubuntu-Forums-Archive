---
title: "Adding a custom keyboard layout"
date: 2013-08-10
forum: General Help
---

### Post by YsWpReA on 2013-08-10
I added the following lines to /usr/share/X11/xkb/symbols/us:

```
partial alphanumeric_keys modifier_keys
xkb_symbols "ioea" {

    name[Group1]= "English (Ioeanths)";

    include "us"
    key <AD01> { [      p,          P,                    6] };
    key <AD02> { [      w,          W,                    4] };
    key <AD03> { [      d,          D,                    0] };
    key <AD04> { [      m,          M,                    2] };
    key <AD05> { [      c,          C,                    8] };
    key <AD06> { [      z,          Z,                       9] };
    key <AD07> { [      g,          G,                    3] };
    key <AD08> { [      r,          R,                    1] };
    key <AD09> { [      f,          F,                   5] };
    key <AD10> { [      y,          Y,                    7] };
    key <AD11> { [     minus,      underscore,      dollar] };
    key <AD12> { [     asciitilde, ampersand,  asciicircum] };

    key <AC01> { [      i,          I,                equal] };
    key <AC02> { [      o,          O,            braceleft] };
    key <AC03> { [      e,          E,          bracketleft] };
    key <AC04> { [      a,          A,            parenleft] };
    key <AC05> { [      u,          U,               exclam] };
    key <AC06> { [      l,          L,           numbersign] };
    key <AC07> { [      n,          N,           parenright] };
    key <AC08> { [      t,          T,         bracketright] };
   key <AC09> { [      h,          H,           braceright] };
    key <AC10> { [     s,          S,                   at] };
    key <AC11> { [     semicolon,  colon,          percent] };

    key <AB01> { [      k,                                 K] };
    key <AB02> { [      j,                                J] };
    key <AB03> { [      b,          B,             asterisk] };
    key <AB04> { [      period,     less,              plus] };
    key <AB05> { [      slash,                     question] };
    key <AB06> { [      comma,                      greater] };
    key <AB07> { [      v,                               V] };
    key <AB08> { [     apostrophe,                 quotedbl] };
    key <AB09> { [     x,                               X] };
    key <AB10> { [     q,                                Q] };
    key <BKSL> { [     backslash,  bar,              grave] };

    include "level3(ralt_switch)"
};
```

I've never made a custom layout in Linux before, but I created that  based on what I've read in a few articles. I added the following to  /usr/share/X11/xkb/rules/xfree86.lst after ! variant:

```
ioea            us: English (Ioeanths)
```

and the following to xfree86.xml under the us layout:

```
<variant>
          <configItem>
            <name>ioea</name>
         <shortDescription>ioea</shortDescription>
            <description>English (Ioeanths)</description>
          </configItem>
        </variant>
```

Now, when I go into preferences>keyboards>layouts>add, even  after restarting X my layout does not show up. How can I get my custom  layout to appear?

---

