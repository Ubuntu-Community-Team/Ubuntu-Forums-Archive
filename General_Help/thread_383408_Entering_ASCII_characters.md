---
title: "Entering ASCII characters"
date: 2007-03-13
forum: General Help
---

### Post by Patrick K on 2007-03-13
How do you enter ASCII characters into a text editor. In Windows holding the alt key and entering the character code enters the character. For example 0163 is the ASCII code for the British Pound character and 0169 is the copyright symbol (C inside a circle). How are these entered in Ubuntu?

---

### Post by stylishpants on 2007-03-13
[http://en.wikipedia.org/wiki/Unicode#Input_methods](http://en.wikipedia.org/wiki/Unicode#Input_methods)

Quote:
[INDENT]
GNOME provides a 'Character Map' utility (Applications/Accessories/Character Map) which displays characters ordered by Unicode block or by writing system, and allows searching by character name or extended description. Where the character's code point is known, it can be entered in accordance with ISO 14755: hold down Ctrl and Shift and enter the hexadecimal Unicode value, preceded by the letter U if using GNOME 2.15 or later. The input code is an UTF-32 value. 
[/INDENT]

For example, type Ctrl+Shift+U30AD to type a Katakana letter Ki. This means, press and hold Ctrl and Shift, then press and release each of the keys u30ad in turn, then release Ctrl and shift.

In Windows you enter the decimal value, but here you're entering the hexadecimal value (which is good, because it's usually shorter to type.)  You can translate between decimal and hexadecimal with the 'calculator' utility (use the 'scientific' setting).  This reveals the following:
    British pound - decimal 0163 - hex A3 
    Copyright symbol - decimal 0169 - hex A9 

Alternatively you can find the hex value just by clicking on the symbol in Character map.  (You probably want to choose the 'Common' script from the left-side menu.)

Note that the article also provides special methods to input characters at the Linux terminal and in the Vim editor (as well as other operating systems.)

---

### Post by Patrick K on 2007-03-13
That works, thanks.

---

### Post by 484 on 2008-04-06
Every time I hit CTRL-SHIFT, Ubuntu changes the language set I'm using. (A little box appears in the lower right with the name of the language e.g. arameic, it has a few clickable buttons on it)

I used the Ubuntu instructions on this website [http://ccat.sas.upenn.edu/~nsivin/chinp.html](http://ccat.sas.upenn.edu/~nsivin/chinp.html)

---

