---
title: "Embed a Tab within a String ?"
date: 2008-02-22
forum: General Help
---

### Post by drs305 on 2008-02-22
How do you embed a tab character in a string? More specifically, I want to enter "ca" then a TAB character then "multi" in a gconf entry that will accept only a string, with the final result looking like "ca    multi". There cannot be any spaces, only a tab character.

It is to be embedded in the following line:
```

gconftool-2 --type list --list-type string --set /desktop/gnome/peripherals/keyboard/kbd/layouts [us,"ca    multi"]

```

I don't know if it is possible to do what I'm asking - it's not embedded in a bash script so I don't think normal escape sequences will work. There may be a special format and character set known by gconf that will allow me to enter what I want but I've spent several hours searching for an answer and haven't found anything that works.

The purpose of this exercise is to create two shortcuts to allow changing the keyboard from US to Canada Multilingual, but it's become more an academic search for an answer at this point.

Thank you.

---

### Post by yabbadabbadont on 2008-02-22
Try using the C escape sequence.  I don't know if it will work, but it is something to try.

"ca\tmulti"

---

### Post by mbsullivan on 2008-02-23
Hi All,

I don't think a pure C-style escape sequence character will work. You could always try:

```
gconftool-2 --type list --list-type string --set /desktop/gnome/peripherals/keyboard/kbd/layouts [us,"`echo -e "ca\tmulti"`"]
```

This should substitute the output of the (escape sequenced) string into your line.

Mike

---

### Post by pointone on 2008-02-23
GConf is just an XML database of settings to be read by a number of applications. The exact "way" to insert a tab depends on the application it's being used for. There's no standard GConf tab besides just hitting the tab key, in this respect. (AFAIK)

Also, remember that all the settings in the GConf database are found in ~/.gconf. You should be able to edit the appropriate file by hand, if necessary.

---

### Post by drs305 on 2008-02-23
Thanks to all of you for your inputs - each of you is correct insofar as what you said. Mike (mbsullivan) wins the prize for giving me the solution to my problem. I still can't enter it directly via the Keyboard preferences or gconf-editor but I can use Mike's input to enclose it in a script which allows the keyboard to change 'on the fly'.

And just for clarification, I typed "ca multi"  but meant "ca multix" for the Canada Multilingual keyboard. The original post is [http://ubuntuforums.org/showthread.php?t=704554](http://ubuntuforums.org/showthread.php?t=704554)

> **mbsullivan said:**
> Hi All,

I don't think a pure C-style escape sequence character will work. You could always try:

```
gconftool-2 --type list --list-type string --set /desktop/gnome/peripherals/keyboard/kbd/layouts [us,"`echo -e "ca\tmulti"`"]
```

This should substitute the output of the (escape sequenced) string into your line.

Mike

---

### Post by mbsullivan on 2008-02-23
Glad I could help =]

Mike

---

