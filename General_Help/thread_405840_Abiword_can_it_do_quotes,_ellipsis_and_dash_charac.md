---
title: "Abiword: can it do quotes, ellipsis and dash characters?"
date: 2007-04-10
forum: General Help
---

### Post by D-- on 2007-04-10
Is it possible to type open and close single/double quotes, em dash, en dash or the ellipsis mark?

Actually, is it possible to type any **standard** typography mark? I searched their list archives and just saw a lot of nasty posts.

You know, for a word processor more advanced than Vi, these are somewhat expected, and other than doing repeat lookups in the character map and pasting them in, I have yet to find a way to type these.

Is there a script for it that can do them as you type?

Do they plan on adding .DOC support? Right now, saving a .DOC just saves a RichText Format file that has its extension changed to .DOC. That's reallllly useful if you have a document with multiple text encodings.

I was expecting a bit more quality from the default text editor shipped with Xubuntu. This is more bare bones than Microsoft Works '95.

---

### Post by rai4shu2 on 2007-04-10
Menu: Insert/Symbol (Ctrl+M)?

---

### Post by D-- on 2007-04-10
I do hope this suggestion was a joke.

They are missing one of the dashes, and the only quote mark within the range shown is a right closing quote. That's not because the font is missing it either. I can import a file saved by OpenOffice, change it to Bitstream Vera Sans, and all its open and close quotes are there.

This is not a viable solution by any stretch. You basically suggested typing ``this''.

You would need to get them from gnome-character-map and paste them in, and to repeat that for every open, close and single quote, em dash, en dash and ellipsis basically takes the "word processing" out of word processing.

I saw some hacking suggestions for changing the [RemapGlyphsTable](http://bugzilla.abisource.com/show_bug.cgi?id=1510) setting, but I can't find it in my ~/.AbiSuite/AbiWord.Profile, and the user offers no help on where to change it.

I'm just extremely disappointed with this being the choice word processor of xubuntu.

---

### Post by rai4shu2 on 2007-04-10
No "Standard Symbols" font on your machine?

---

### Post by D-- on 2007-04-10
Yes. There is Standard Symbols L, which only has one direction. Regardless, this will create a mismatch in typography with the actual document font. I could select the current font, but it doesn't show the range where the quotes are actually accessible.

Is there any real solution for this problem?

(It's worth noting the quote mark included in Standard Symbols L is a right quote.)

---

### Post by rai4shu2 on 2007-04-10
Well, that sucks. I guess Abiword doesn't handle that problem.

---

