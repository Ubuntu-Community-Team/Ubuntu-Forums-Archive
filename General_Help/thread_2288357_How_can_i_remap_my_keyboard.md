---
title: "How can i remap my keyboard?"
date: 2015-07-26
forum: General Help
---

### Post by manu17 on 2015-07-26
[COLOR=#111111][FONT=Ubuntu]Hi i have a little problem with the order of two keys in my keyboard, instead of being [AltGr] +[<>] like in most of the keyboards in my country, my keyboard comes with the keys this way: [<>] + [ AltGr ]. Where each par of brackets represents a key.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To fix it i swapped the physic keys and created a file called .xmodmaprc in my home directory and put this on it:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]keycode 94 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]keycode 108 = less greater[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then i run this command: sudo xmodmap ~/.xmodmaprc[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After running the command i get the AltGr key working okey but i have a problem with the [< >] key, when i press it i get < like it should be but when i press shift + [< >] i get < instead of >.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Do someone know how to fix this?[/FONT][/COLOR]

---

### Post by manu17 on 2015-07-27
Nobody?

---

### Post by HermanAB on 2015-07-27
There are various ways.  You can make a whole new keymap file, or you can just make a few changes after boot up using xmodmap.  Xmodmap is my preferred method, since it is easier to experiment.  

Changing the whole map file may cause you to inadvertently lose control and be unable to type your login and password.  Therefore start your experiments by changing keys that are NOT in your username or password!

For example: [https://wiki.archlinux.org/index.php/Xmodmap](https://wiki.archlinux.org/index.php/Xmodmap)

---

### Post by manu17 on 2015-07-27
If you read ny post, im telling that i tried xmodmap but got that strange error

---

### Post by manu17 on 2015-07-29
Please if someone knows antthing say it!

---

### Post by Bashing-om on 2015-07-29
manu17; Hello;

I do believe that ' xmodmap' is depreciated.
maybe try from 'xkb' tool ?
[http://unix.stackexchange.com/questions/49650/how-to-get-keycodes-for-xmodmap](http://unix.stackexchange.com/questions/49650/how-to-get-keycodes-for-xmodmap)
[http://madduck.net/docs/extending-xkb/](http://madduck.net/docs/extending-xkb/) 

see if 'xkb' does the job for you.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by HermanAB on 2015-07-29
Well, xmodmap and xev still work for me on Ubuntu, but it requires some experimentation to get right.   

If you want to swap two keys, then it requires some shuffling to get it to 'take', i.e. you may have to define something twice.  

For example to swap the A and B keys, you need to do an A = B, B = A, A = B kinda thing.

The good news is that once it works, it will keep working.

The correct way is probably to be sure to 'remove' a key definition before you 'add' it again with a new definition, for example:

remove mod4 = Super_R 
remove mod4 = Super_L 
add Control = Super_R 
add Control = Super_L

---

