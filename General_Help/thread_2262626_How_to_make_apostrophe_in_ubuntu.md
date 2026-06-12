---
title: "How to make apostrophe in ubuntu?"
date: 2015-01-26
forum: General Help
---

### Post by petermartin2 on 2015-01-26
I have tried with english (us) and french layouts and can't make an apostrophe. Anyone have an idea where it is located or how to make it? When I hit the button with that sign on my keyboard it just appears before or after the letter: e´ ´e but I would like to have it above the letter. Anyone has an idea where on what combinations of keys I should press?

---

### Post by Impavidus on 2015-01-26
Are you referring to the acute accent ( ´ )? The apostrophe is this one: ' .

Depending on keyboard layout, there may be precomposed characters, so that's an actual <é> key on your keyboard. Or there may be a <dead acute> key. It seems your acute key produces a living acute. Pressing <dead acute> followed by e will give é. <dead acute>, <space> gives ´. Maybe you can access it using a third level chooser (the <AltGr> key). And what always works is the compose key. Define a compose key, press <compose>, <'>, <e> and you get é (that's how I type this post). If you fancy memorising hexadecimal codes, you can also try <ctrl>+<shift>+<u>, hexadecimal unicode code, <space>

---

### Post by petermartin2 on 2015-01-26
> **Impavidus said:**
> Are you referring to the acute accent ( ´ )? The apostrophe is this one: ' .

Depending on keyboard layout, there may be precomposed characters, so that's an actual <é> key on your keyboard. Or there may be a <dead acute> key. It seems your acute key produces a living acute. Pressing <dead acute> followed by e will give é. <dead acute>, <space> gives ´. Maybe you can access it using a third level chooser (the <AltGr> key). And what always works is the compose key. Define a compose key, press <compose>, <'>, <e> and you get é (that's how I type this post). If you fancy memorising hexadecimal codes, you can also try <ctrl>+<shift>+<u>, hexadecimal unicode code, <space>

Ok it would seem that I have an actual key on the keyboard I will mark thread solved

---

### Post by Peter Maunder on 2015-01-26
There are two areas concerned when typing accented characters, the character set itself and the keyboard layout.

There is a useful Wikipedia entry for US and UK keyboards called AltGr key showing the layouts. However, you may need to define your keyboard to use this AltGr function. On Ubuntu 12.04 UK version I have defined the keyboard as ENGLISH (UK extended Winkeys) on my systems and this supports all the French and most German accents . The default US and UK keyboards do not enable AltGr by default and so there are not keys directly defined to support French. If you are typing French do not forget you also have î ü ç à À Ç etc available with sticky keys. French keyboards have totally different layout and you should be careful trying to emulate them on a US or UK keyboard.   
I do know some users of US keyboards define them as Canadian to get support for accents.
Do not forget that if you define your character set as US-ASCII, which some e-mail systems do, this supports only the first 127 characters and they do not include any accented characters. So you sometimes see characters like &#65533; where the character you have typed is not supported by the character set, hence you can&#65533;t type the '.

---

