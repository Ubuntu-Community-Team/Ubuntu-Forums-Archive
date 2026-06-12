---
title: "xmodmap not retained on change of input method"
date: 2014-08-24
forum: General Help
---

### Post by James Wilde on 2014-08-24
I have configured a modification to the standard Swedish keyboard so that one dead key creates other symbols than those shown on the keyboard.  Thus the key two to the right of the 'P' key should have the symbols " ^ and ~, that is the umlaut (two dots over e.g. the german a and o), the circumflex, often used in french to indicate a missing letter (most commonly 'S', I believe), and the thingummy over 'N' in spanish that turns it into something that sounds like 'ny'.  These three symbols are produced with the key alone, key+shift and key+altgr respectively.

I have changed this with xmodmap so that ^ is replaced by &#711;, an upside down circumflex and ~ is replaced by ¯.  These two symbols are needed when I type pinyin, the method of writing chinese using western letters and four accents.  On my system I also have two varieties of pinyin as my input method, so-called intelligent pinyin and ordinary pinyin.  These take pinyin input and generate chinese symbols so that if I type q&#299;ngwèn on the keyboard I get &#35831;&#38382; in my document.

Previously (in 13.10) when I changed from swedish input method to one of these two pinyin methods and then changed back, I am certain that the system remembered my modified keyboard and I could continue writing with my personal symbols.  Now, since the upgrade to 14.04, the keyboard modifications are lost on returning from pinyin to swedish.  It is the same whether I use the input method icon in the menu bar or the super+space and shift+super+space to change input methods.  Instead I have to re-run my script to set up the modified keyboard.

This is very inconvenient, since I spend a lot of time preparing tables of translations, where I have first the english word or phrase, then the equivalent in pinyin (where I need my modified keyboard) and finally the chinese symbols themselves, for which I have to change input method.  I then change back for the next row, and have to reload my xmodmap.

I would like to say that this is a bug which crept in when 14.04 was released.  Can anyone confirm that the keyboard was maintained under 13.10 when changing input method?

---

