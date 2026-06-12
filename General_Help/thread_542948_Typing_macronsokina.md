---
title: "Typing macrons/okina"
date: 2007-09-04
forum: General Help
---

### Post by Ace02 on 2007-09-04
Aloha k&#257;kou,

I recently installed Ubuntu 7.04 on a partition, and I'm loving it. The only thing I'm missing is the ability to type macron vowels (&#256; &#257; &#274; &#275; &#298; &#299; &#332; &#333; &#362; &#363;) and the Okina ( &#699; ) for the Hawai&#699;ian language. On my Windows XP partition I've downloaded a keyboard definition that allows me to just hold down the right alt key to type these. For example, holding the right alt and pressing the "o" key results in a "&#333;." I'm using the character palette right now, which is ok, but I just can't make them very quickly while I'm typing. Does anyone know of a tweak/app I can use to get something similar to my XP setup?

Mahalo,

Kyle

---

### Post by kapali on 2008-06-04
I am able to type the kahako on ubuntu and fedora doing this:

1) add the following line to /etc/environment

GTK_IM_MODULE="xim"

2) Set the <multi_key> (I use the right windows key)

System -> Preferences -> Keyboard -> Layout -> Layout Options -> Compose Key Positions

3) (I had to re-login at this point)

From most applications, you get the macron by this sequence (just press each key in sequence, no need to hold them down simultaneously)

a) right windows key
b) - (the dash, on same key as the underscore character)
c) vowel, e.g. &#257; &#275; &#299; &#333; &#363;

4) For the okina, there is no character mapped in X for the true okina (unicode: \x{2BB} html: &#699;) value, but the left single apostrophe does look the same:

a) right windows key
b) <
c) ' (apostrophe)

This works within open office as well as xterm and most text editors. Some applications, such as First Class (Leoki) on Linux will not display this correctly.  It would be good to add the true okina \x{02BB} to the xim encodings, but I am not sure how to do this without re-compiling X.

me ke aloha,
Kapali

---

