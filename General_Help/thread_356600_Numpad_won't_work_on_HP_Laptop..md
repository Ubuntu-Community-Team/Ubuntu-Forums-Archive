---
title: "Numpad won't work on HP Laptop."
date: 2007-02-08
forum: General Help
---

### Post by GI_Josh on 2007-02-08
Hey guys.  I have an HP dv8000 laptop that includes a numpad.  However, ubuntu won't recognize my numpad, I can't use it.  and yes, I made sure numlock is on  :-)  Does anyone know why this is happening?

---

### Post by dannyboy79 on 2007-02-08
because laptop's are all different as far as what keys they have and which they don't have. I mean, I know they all have the normal ones, but some have number keypads etc etc. you're going to have to map them in order to get them to work. unless of course you're talking about the number keys directly above your top row of letters. if that's the case, than it sounds like you may have chosen the wrong keyboard layout. you'll have to gogle laptop keys and ubuntu and I am sure you;ll find an answer. 

like here is a possible solution: [http://www.ubuntuforums.org/archive/index.php/t-6204.html](http://www.ubuntuforums.org/archive/index.php/t-6204.html)

---

### Post by GI_Josh on 2007-02-08
Its the numpad, not the numbers above the letters.  I don't really understand, how do I go about mapping the keys?

---

### Post by dannyboy79 on 2007-02-09
this is all explained within the link I provided. You'll need to READ and LEARN how to do it. Here is a clip from that link:

First, you have to know the keycodes. In a terminal start xev, move mouse to black square and press this buttons. Keycodes will appear in term. Then install hotkeys. You have to edit the keyboard file (xml).

It has to do with finding out what codes go with which keys and then mapping them in correctly.

---

