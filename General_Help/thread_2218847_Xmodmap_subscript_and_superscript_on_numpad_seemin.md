---
title: "Xmodmap: subscript and superscript on numpad seemingly impossible?!"
date: 2014-04-22
forum: General Help
---

### Post by kiwi_kirsch on 2014-04-22
i would LOVE to be able to easily write decimal fractures.

superscript numbers, &#8260; and subscript numbers, mainly for all those inch numbers in bicycle mechanics, looking like this number and size of bearing balls i needed: 20× ³&#8260;&#8321;&#8326;"

what i would like to make work is this:
[B]
keycode  79 = 7 7 7 7 U2087 U2077 U2087 U2077
keycode  80 = 8 8 8 8 U2088 U2078 U2088 U2078
keycode  81 = 9 9 9 9 U2089 U2079 U2089 U2079
keycode  83 = 4 4 4 4 U2084 U2074 U2084 U2074
keycode  84 = 5 5 5 5 U2085 U2075 U2085 U2075
keycode  85 = 6 6 6 6 U2086 U2076 U2086 U2076
keycode  87 = 1 1 1 1 U2081 U2071 U2081 U2071
keycode  88 = 2 2 2 2 U2082 U2072 U2082 U2072
keycode  89 = 3 3 3 3 U2083 U2073 U2083 U2073
keycode  90 = 0 0 0 0 U2080 U2070 U2080 U2070[/B]

which simply won't.

i have adjusted LOTS of symbols in my xmodmap, yet those ²³ and[SIZE=1] &#8322;&#8323;[/SIZE] won't show up with ANY key combination pressed.

keysyms 1, 2, 5 and 6 do work, though, with ANY OTHER key pressed. only that number block on the right hand won't work with »altgr«. is there any speciality to obey over there? or do i just not see an obvious mistake i made? 

i also tried

**keycode  88 = 2 2 U2082 U2072 U2082 U2072**

and

**keycode  88 = 2 2 2 2 U2082 U2072**

but none else than this

**keycode  88 = U2082 U2072**

showed me those little numbers. ANY other setting types normal big numbers with ANY key combination pressed.

[IMG]http://smilies.kiwikirsch.de/panic.gif[/IMG]

[typo edit]

---

### Post by kiwi_kirsch on 2014-04-24
no one knows..? :(

---

