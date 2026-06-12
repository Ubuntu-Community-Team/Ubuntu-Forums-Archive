---
title: "Typing in Esperanto"
date: 2007-05-16
forum: General Help
---

### Post by kinghajj on 2007-05-16
I was glad to find that Ubuntu has an Esperanto layout, but found that it is difficult to use. Instead of assigning the 'hat' characters to keys, is there a way to automatically substitute a key sequence  to a 'hat' character? (For example, typing 'cx' would change to '&#265;'.) I tried to find guides for writing keyboard layouts, but couldn't find information on this kind of substitution.

And if it matters, I use a Dvorak layout currently.

---

### Post by Masoris on 2007-06-25
I had exactly same problem with you. Finally I found a esperantisto *Mythos* in *Lernu.net* who use Dvorak layout in Kubuntu. I copied the messages below. I hope it helps you.

-------------------------------------

From:  	 Mythos
Date: 	2007-05-21 1:57:46
Subject: 	Re: Esperanto in Ubuntu.
 
>Hi. I heard that you are use esperanto with dvorak layout in Kubuntu. I'm using Ubuntu feisty with dvorak layout, but I have no idea how can I input esperanto in dvorak. Do you know something way?

Yes I do. It involves editing some of the system files. You will need to find the proper xkb layout file (mine is /etc/X11/xkb/symbols/us ), then you will need to find the dvorak section and replace it with the code that I attached below (always be sure to make a copy of the file that you are changing, just in case something goes wrong). This will allow you to type Esperanto characters when you select your third level switcher (mine is the right alt key). Let me know if you have any questions.

// Starting the code:

xkb_symbols "basic" {

name[Group1]= "Dvorak";

// Alphanumeric section

key { [ grave, asciitilde, dead_grave, dead_tilde ] };

key { [ 1, exclam ] };
key { [ 2, at ] };
key { [ 3, numbersign ] };
key { [ 4, dollar, cent] };
key { [ 5, percent ] };
key { [ 6, asciicircum, dead_circumflex, dead_circumflex ] };
key { [ 7, ampersand ] };
key { [ 8, asterisk ] };
key { [ 9, parenleft, dead_grave] };
key { [ 0, parenright ] };
key { [ bracketleft, braceleft ] };
key { [ bracketright, braceright, dead_tilde] };

key { [ apostrophe, quotedbl, dead_acute, dead_diaeresis ] };
key { [ comma, less, dead_cedilla, dead_caron ] };
key { [ period, greater, dead_abovedot, periodcentered ] };
key { [ p, P ] };
key { [ y, Y, yen ] };
key { [ f, F ] };
key { [ g, G, gcircumflex, Gcircumflex ] };
key { [ c, C, ccircumflex, Ccircumflex ] };
key { [ r, R, registered, copyright] };
key { [ l, L ] };
key { [ slash, question ] };
key { [ equal, plus ] };

key { [ a, A, ae, AE ] };
key { [ o, O ] };
key { [ e, E, EuroSign, cent ] };
key { [ u, U, ubreve, Ubreve ] };
key { [ i, I ] };
key { [ d, D ] };
key { [ h, H, hcircumflex, Hcircumflex ] };
key { [ t, T ] };
key { [ n, N ] };
key { [ s, S, scircumflex, Scircumflex ] };
key { [ minus, underscore ] };

key { [ semicolon, colon, dead_ogonek, dead_doubleacute ] };
key { [ q, Q ] };
key { [ j, J, jcircumflex, Jcircumflex ] };
key { [ k, K ] };
key { [ x, X ] };
key { [ b, B ] };
key { [ m, M ] };
key { [ w, W, ubreve, Ubreve ] };
key { [ v, V ] };
key { [ z, Z ] };

};

// End code:

------------------------------

Sent to:  	Mythos
Date: 	2007-05-29 4:18:08
Subject: 	Re: Re: Esperanto in Ubuntu.
 
Thank you. I can type esperanto with dvorak layout now

But your code didn't work in my Ubuntu, So I made a new code myself.

partial alphanumeric_keys
xkb_symbols "dvorak" {

name[Group1]= "U.S. English - Dvorak";

// Alphanumeric section

key { [ grave, asciitilde, dead_grave, dead_tilde ] };

key { [ 1, exclam ] };
key { [ 2, at ] };
key { [ 3, numbersign ] };
key { [ 4, dollar ] };
key { [ 5, percent ] };
key { [ 6, asciicircum, dead_circumflex, dead_circumflex ] };
key { [ 7, ampersand ] };
key { [ 8, asterisk ] };
key { [ 9, parenleft, dead_grave] };
key { [ 0, parenright ] };
key { [ bracketleft, braceleft ] };
key { [ bracketright, braceright, dead_tilde] };

key { [ apostrophe, quotedbl, dead_acute, dead_diaeresis ] };
key { [ comma, less, dead_cedilla, dead_caron ] };
key { [ period, greater, dead_abovedot, periodcentered ] };
key { [ p, P ] };
key { [ y, Y ] };
key { [ f, F ] };
key { [ g, G, gcircumflex, Gcircumflex ] };
key { [ c, C, ccircumflex, Ccircumflex ] };
key { [ r, R, registered, copyright ] };
key { [ l, L ] };
key { [ slash, question ] };
key { [ equal, plus ] };

key { [ a, A ] };
key { [ o, O ] };
key { [ e, E, EuroSign, cent ] };
key { [ u, U, ubreve, Ubreve ] };
key { [ i, I ] };
key { [ d, D ] };
key { [ h, H, hcircumflex, Hcircumflex ] };
key { [ t, T ] };
key { [ n, N ] };
key { [ s, S, scircumflex, Scircumflex ] };
key { [ minus, underscore ] };

key { [ semicolon, colon, dead_ogonek, dead_doubleacute ] };
key { [ q, Q ] };
key { [ j, J, jcircumflex, Jcircumflex ] };
key { [ k, K ] };
key { [ x, X ] };
key { [ b, B ] };
key { [ m, M ] };
key { [ w, W, ubreve, Ubreve ] };
key { [ v, V ] };
key { [ z, Z ] };
};

---

### Post by Sonja on 2007-12-27
key { [ g, G, gcircumflex, Gcircumflex ] };

What special key do I press to get the circumflex version? Is it right-alt or a deadkey or something?

Also how do I modify this layout to produce IPA characters? Why do you type out "gcircumflex" in full instead of just "&#285;"? If I want to have IPA symbols available, do I type some sort of longname (if so where is the full list?) or can I just directly paste in a character like "&#601;"?

Multan dankon!!!!

Sonja

---

### Post by donmiguel on 2008-02-13
key { [ g, G, gcircumflex, Gcircumflex ] };

what you must hit to get:
for g: hit g
for G: hit G
(now it gets tricky :) )
for &#285;: alt gr + g
for &#284;: alt gr + shift + g

for my part, i just looked up the layout i was using and modified it by simply adding the special characters to the corresponding letter, so there's now drawback on xyw etc :)

here's is what i once wrote on another board:

[QUOTE="another board :)"]
The manipulation is quite easy! You can study the keyboard layouts in the directory: /usr/share/X11/xkb/symbols. Note, that you can include designs and then alter them, and finally have to declare them (such as name[Groupe1]=..)

Then you have to tell X that there is another keyboard layout. You do that in /usr/shar/X11/rules/xorg.xml & xorg.lst (they are self-explaining)

be careful tough! And back the files up..

You could as well design a new keyboard instead of adding one. I edited the swiss-german (ch_de) keyboard-file and added a further designs (to the already existing 8 :) I called it Switzerland - German, plus esperanto letters

further reading:

[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)
[http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)

the result: 
[http://eo.lernu.net/komunikado/forumo/dosieroj/31478-c3327a-955.png](http://eo.lernu.net/komunikado/forumo/dosieroj/31478-c3327a-955.png)
[/QUOTE]

---

