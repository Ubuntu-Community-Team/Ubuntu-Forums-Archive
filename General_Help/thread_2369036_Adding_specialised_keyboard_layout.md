---
title: "Adding specialised keyboard layout"
date: 2017-08-17
forum: General Help
---

### Post by mats.kober on 2017-08-17
Hi,
Installed Ubuntu 16.04 LTS some month ago, as a preparation for a migration from Windows. I am in need of easy access to braille characters,  a customised keyboard layout with utf-8 Braille Characters in the six-dots range. I use a standard Norwegian laptop keyboard (ThinkPad L460). I have tried a 'Keyboard Layout Editor' I found recommended somewhere, but ended up writing a layout form "scratch" - based upon the structure on the files I found in the files in  /usr/share/X11/xkb/symbols. But I am having problems installing it. I have added the file in the lists in /usr/share/X11/xkb/rules/base.xml and /usr/share/X11/xkb/rules/base.xml; I find the layout in the list over available text-entries. But it do not work. No Braille Characters, just the normal once. Been googling it, and have tried a lot of different commands in terminal, to reset this and that; I've even been deleting files manually somewhere - following some advice in some tread. I was not allowed to upload the file, but here is ow it looks:

```
[default  partial alphanumeric_keysxkb_symbols "braille" {


name[Group1]= "braille (Norwegian six-dots)";


key <TLDE> { [     ,     ,     ,     ] };
key <AE01> { [    ,     ,     ,     ] };
key <AE02> { [    U2832,     ,     ,     ] };
key <AE03> { [    U283C,     ,     ,     ] };
key <AE04> { [     ,     ,     ,     ] };
key <AE05> { [     ,     ,     ,     ] };
key <AE06> { [     ,     ,     ,     ] };
key <AE07> { [    U2814,     ,     ,     ] };
key <AE08> { [    U2826,     ,     ,     ] };
key <AE09> { [    U2834,     ,     ,     ] };
key <AE10> { [    U2836,     ,     ,     ] };
key <AE11> { [    U2822,     ,     ,     ] };
key <AD01> { [    U281F,     ,     ,     ] };
key <AD02> { [    U283A,     ,     ,     ] };
key <AD03> { [    U2811,    U283F,    U282E,    U2823] };
key <AD04> { [    U2817,     ,     ,     ] };
key <AD05> { [    U281E,     ,     ,     ] };
key <AD06> { [    U283D,     ,     ,     ] };
key <AD07> { [    U2825,    U2833,    U283B,     ] };
key <AD08> { [    U280A,     ,     ,     ] };
key <AD09> { [    U2815,    U282C,    U283E,     ] };
key <AD10> { [    U280F,     ,     ,     ] };
key <AD11> { [    U2821,     ,     ,     ] };
key <AD12> { [    U2808,    U2818,    U2828,     ] };
key <AC01> { [    U2801,    U2837,     ,     ] };
key <AC02> { [    U280E,    U2831,     ,     ] };
key <AC03> { [    U2819,    U2839,     ,     ] };
key <AC04> { [    U280B,     ,     ,     ] };
key <AC05> { [    U281B,     ,     ,     ] };
key <AC06> { [    U2813,     ,     ,     ] };
key <AC07> { [    U281A,     ,     ,     ] };
key <AC08> { [    U2805,     ,     ,     ] };
key <AC09> { [    U2807,     ,     ,     ] };
key <AC10> { [    U282A,     ,     ,     ] };
key <AC11> { [    U281C,     ,     ,     ] };
key <BKSL> { [    U2810,    U2814,     ,     ] };
key <LSGT> { [    U2820,    U2830, U2800,     ] };
key <AB01> { [    U2835,     ,     ,     ] };
key <AB02> { [    U282D,     ,     ,     ] };
key <AB03> { [    U2809,    U282F,    U2829,     ] };
key <AB04> { [    U2827,     ,     ,     ] };
key <AB05> { [    U2803,     ,     ,     ] };
key <AB06> { [    U281D,    U282B,     ,     ] };
key <AB07> { [    U280D,     ,     ,     ] };
key <AB08> { [    U2802,    U2806,     ,     ] };
key <AB09> { [    U2804,    U2812,     ,     ] };
key <AB10> { [    U2824,    U2838,     ,     ] };


};
```

---

### Post by ajgreeny on 2017-08-18
There is a number of packages in the repos with **braille** in their names; whether or not you need any of those is something I can not answer, but it may be a necessity if you need to use any braille utilities.

The easiest way to find them all may be to use synaptic and search for "braille" using name only.

---

### Post by mats.kober on 2017-08-21
Thanks for feedback. Not sure if this is a "Braille problem", though: The problem seems to be (for a novise like me) that the keyboard layout is not implemented or something? Is there a "memory" somewhere, some temporary files or something, that needs to be updated?

---

