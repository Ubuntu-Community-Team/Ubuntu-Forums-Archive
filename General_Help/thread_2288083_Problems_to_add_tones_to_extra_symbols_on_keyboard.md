---
title: "Problems to add tones to extra symbols on keyboard (XKB)"
date: 2015-07-24
forum: General Help
---

### Post by mats-gbproject on 2015-07-24
Hi


I've just started to learn about XKB.

I work on a project for local languages in Togo, we're working on 25 languages there ([en.globalbility.org]("http://en.globalbility.org")).  We want to make a new keyboard that are based on the French one that  include symbols for local languages. I've tested with the XKB system  inside Ubuntu and made a first test keybord (really not final version,  just to test it).


I have problem as there are several of the languages use tones on their symbols like acute accent ( ´ ), grave accent ( **`** ), circumflex ( **ˆ **) tilde ( **~ **) and macron ( ¯ ) on top of them.


Here are the extra symbols I've added to the keyboard:
&#658; &#603; &#477; &#436; &#651; &#617; &#596; &#650; &#599; &#598; ƒ &#611; &#614; &#626; &#595; &#331;


It should be possible to write them like this (examples from texts we have produced):
&#8055; &#596;&#769; &#603;&#769; 
&#603;&#768; &#596;&#768;
&#596;&#771; &#603;&#771; &#596;&#771; &#297;
&#603;&#772;
î


How can I modify these kinds of combination symbols?

I  try to click AltGr+` and after AltGr+&#603; to get &#603;&#768;, but then noting  happens, and after I only get &#603; (without grave accent). Why? Is it  because the keyboard misunderstand when I click AltGr two times? How  can I solve this?


Here is the small file I made to test it:

```
[COLOR=#660000]default  partial alphanumeric_keys
xkb_symbols "basic" {

    // First we include the whole French keyboard
    include "fr"

    // We give our new keyboard a name
    name[Group1]="French (Togo)";

    // Then we start to change the keys on the French keyboard.
    // Each key have a unique number.
    // Each key have 4 values: default, shift, altgr, shift+altgr  (altgr is the right side 'alt' key)

    // First row


    // Second row
    key <AD02>    { [    z,    Z,    U0292,    U01B7 ] };    // U0292 = &#658; (small), U01B7 = &#439; (capital)
    key <AD03>    { [    e,    E,    U025B,    U0190 ]    };    // U025B = &#603; (small), U0190 = &#400; (capital)
    key <AD04>    { [    r,    R,    U01DD,    U018E ] };    // U01DD = &#477; (small), U018E = &#398; (capital)
    key <AD06>    { [    y,    Y,    U01B4,    U01B3 ] };    // U01B4 = &#436; (small), U01B3 = &#435; (capital)
    key <AD07>    { [    u,    U,    U028B,    U01B2 ] };    // U028B = &#651; (small), U01B2 = &#434; (capital)
    key <AD08>    { [    i,    I,    U0269,    U0196 ] };    // U0269 = &#617; (small), U0196 = &#406; (capital)
    key <AD09>    { [    o,    O,    U0254,    U0186 ] };    // U0254 = &#596; (small), U0186 = &#390; (capital)

    // Third row
    key <AC01>    { [    q,    Q,    U028A,    U01B1 ] };    // U028A = &#650; (small), U01B1 = &#433; (capital)
    key <AC02>    { [    s,    S,    U0257,    U018A ] };    // U0257 = &#599; (small), U0189 = &#394; (capital)
    key <AC03>    { [    d,    D,    U0256,    U0189 ] };    // U0256 = &#598; (small), U0189 = &#393; (capital)
    key <AC04>    { [    f,    F,    U0192,    U0191 ] };    // U0192 = ƒ (small), U0191 = &#401; (capital)
    key <AC05>    { [    g,    G,    U0263,    U0194 ] };    // U0263 = &#611; (small), U0194 = &#404; (capital)
    key <AC06>    { [    h,    H,    U0266,    U0124 ] };    // U0266 = &#614; (small), U0124 = &#292; (capital)
    key <AC10>    { [    m,    M,    U0272,    U019D ] };    // U0272 = &#626; (small), U019D = &#413; (capital)


    // Fourth row
    key <AB05>  { [    b,    B,    U0253,    U0181 ] };    // U0253 = &#595; (small), U0181 = &#385; (capital)
    key <AB06>    { [    n,    N,    U014B,    U014A ] };    // U014B = &#331; (small), U014A = &#330; (capital)


};[/COLOR]


```

---

### Post by mats-gbproject on 2015-10-09
XKB patches should apparently be submitted here:
[https://bugs.freedesktop.org/enter_bug.cgi?product=xkeyboard-config](https://bugs.freedesktop.org/enter_bug.cgi?product=xkeyboard-config)

Here is my patch:
[https://bugs.freedesktop.org/show_bug.cgi?id=92344](https://bugs.freedesktop.org/show_bug.cgi?id=92344)

---

### Post by mats-gbproject on 2015-10-09
Tones (Combination keys) needs to be added to gnome:
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

