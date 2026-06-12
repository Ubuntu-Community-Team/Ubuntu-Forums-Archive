---
title: "How to write inverted question and exclamation marks ¿ ¡ in Ubuntu"
date: 2014-07-24
forum: General Help
---

### Post by shantiq on 2014-07-24
[B]Best and quickest ! using [Fourth Level Choosers]("https://help.ubuntu.com/community/ComposeKey#Third_and_fourth_level_choosers")

[COLOR=#252525][FONT=sans-serif]Press AltGr+Shift[held in]+1 to get ¡[/FONT][/COLOR]
[/B][COLOR=#252525][FONT=sans-serif][AltGr [/FONT][/COLOR]**then **[COLOR=#252525][FONT=sans-serif]Shift and hold them in]
[/FONT][/COLOR]**[B]Press AltGr+Shift[held in]+- to get ¿**[COLOR=#000000]



[/COLOR][/B][COLOR=#000000][B]or   more difficult 
[/B]
on Ubuntu press CTRL+SHIFT keep them in , press U and release U then following numbers and letters and release CTRL+SHIFT; then letter/symbol appears

¿ 00BF
¡ 00A1

of use too maybe

ç 00E7
à 00E0
á 00E1
â 00E2
ã 00E3
ä 00E4
æ 00E6
è 00E8
é 00E9
ê 00EA
ë 00EB
î 00EE
ï 00EF
ô 00F4
õ 00F5
ö 00F6
ù 00F9
ú 00FA
û 00FB
ü 00FC
ñ 00F1

**Use Accessories/CharacterMap **to find code numbers for all letters/symbols
if looking for more use this site [/COLOR][[COLOR=#000000]http://www.fileformat.info/info/unicode/char/search.htm[/COLOR]]("http://www.fileformat.info/info/unicode/char/search.htm")

ALSO a Must  >>>>  [SIZE=4][&#9679;&#9679;&#9679;&#9679;]("https://help.ubuntu.com/community/GtkComposeTable")[/SIZE]

Now also all summarized on [Wikipedia]("https://en.wikipedia.org/wiki/Inverted_question_and_exclamation_marks#Input_methods_for_Ubuntu_Linux")

---

### Post by Impavidus on 2014-07-24
I always recommend the compose key (which you have to configure first):
Compose ? ? &#8594; ¿
Compose ! ! &#8594; ¡
(using Compose - > &#8594; &#8594;)

The same way:```

ç ,c   â ^a   æ ae   ê ^e   ï "i   ö "o   û ^u
à `a   ã ~a   è `e   ë "e   ô ^o   ù `u   ü "u
á 'a   ä "a   é 'e   î ^i   õ ~o   ú 'u   ñ ~n
```Easier to remember than hexadecimal codes.

---

### Post by shantiq on 2014-07-26
Just found an even quicker way

[B]using [Fourth Level Choosers]("https://help.ubuntu.com/community/ComposeKey#Third_and_fourth_level_choosers")

[/B]Press AltGr+Shift[held in]+1 to get ¡
[AltGr **then** Shift and hold them in]
Press AltGr+Shift[held in]+- to get ¿

edit to original post

---

### Post by shantiq on 2014-07-26
Another route as Impavidus suggested



First set the compose key:

```
sudo leafpad /etc/default/keyboard

```

and change to



```
XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
[COLOR=#b22222]**XKBOPTIONS="compose:Shift+AltGr"**   #use another key if you wish list here [/COLOR][http://www.autohotkey.com/docs/KeyList.htm](http://www.autohotkey.com/docs/KeyList.htm)



```


[B]Now you need to logout and login again to activate

press Shift then AltGr   and you are ready
[/B]
Then you can use chart provided by Impavidus

ç ,c 
  â ^a 
  æ ae 
  ê ^e
   ï "i 
  ö "o 
  û ^u
à `a 
  ã ~a 
  è `e 
  ë "e 
  ô ^o 
  ù `u 
  ü "u
á 'a 
  ä "a 
  é 'e 
  î ^i 
  õ ~o 
  ú 'u 
  ñ ~n


=====


also


Press AltGr+Shift[held in]+c to get © or Shift+AltGr [release]then o c to get ©


Shift+AltGr [release]then ' e to get é
Shift+AltGr [release]then ` e to get è


===========================
[COLOR=#3E3E3E]**Or still** Using a Spanish Keyboard Layout just for those ¡¿ signs[/COLOR]





Easy enough ... add keyboard layout for Spanish 

then use this key [ATTACH=CONFIG]255124[/ATTACH] +gives ¡ =gives ¿



on LXDE toggle through layouts with Shift+CapLock easy to do
[ATTACH=CONFIG]255123[/ATTACH]

---

