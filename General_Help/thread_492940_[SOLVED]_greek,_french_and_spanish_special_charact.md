---
title: "[SOLVED] greek, french and spanish special characters on a swiss keyboard with scim"
date: 2007-07-05
forum: General Help
---

### Post by doncristobal on 2007-07-05
Hello everyone

My scim (on xubuntu 7.04) lets me type in korean (&#54620;&#44544;), greek (&#945;&#946;&#947;...) and latin characters after some struggle... 

BUT: greek, spanish and french special characters are not possible! i get ö&#945; or ´&#945; instead of the proper &#945; with the accent ´ on top of it. or ~n instead of the proper spanish n with the little wave on top. 

My previous xubuntu installation allowed me to input those special characters with scim set to English/European as well as to greek (M17N-el-kbd). 

I have a swiss german keyboard where plenty of things like ´ ~ ^ ` ¨ usually can be typed before the letter on which they should end up. 

Does anyone have a hint? Thank you very much!

---

### Post by bapoumba on 2007-07-05
May be look at the "compose" key. To activate it in Xfce, you have to change your /etc/X11/xorg.conf (there may be other ways to do it, but did not find them):
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbOptions"    "lv3:ralt_switch, compose:rwin"
EndSection

```
Last line. I assigned it to the right Windows key.

With an azerty keyboard, fr layout:
<compose> + ~ + n = ñ
<compose> + ~ + <maj> n = Ñ.

May be you can give it a shot.

---

### Post by doncristobal on 2007-07-05
merci beaucoup!

I'll be happy to try this, but my ibm notebook does not have any windows keys... there is a back key that linux does not use - how do i find out what my last line should say? 

I assume i'll have to adapt it somehow like that: 
>         Option          "XkbOptions"    "lv3:ralt_switch, compose:=>back<="
where =>back<= should be the code for my back key?

Thank you to anyone who can give advice!


by the way, the section in my xorg.conf: 
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ch"
        Option          "XkbVariant"    "de_nodeadkeys"
EndSection

```

---

### Post by bapoumba on 2007-07-05
De rien !

Sorry, I had to look around...
In /usr/share/X11/xkb/rules/xorg.lst, I have (close to the bottom of the file):
```

Compose key          Compose key position
  compose:ralt         Right Alt is Compose.
  compose:lwin         Left Win-key is Compose.
  compose:rwin         Right Win-key is Compose.
  compose:menu         Menu is Compose.
  compose:rctrl        Right Ctrl is Compose.
  compose:caps         Caps Lock is Compose.
```
So I guess these are the possible options by default to set the "compose" key. Do you have a rctrl or a menu key? (menu is, on my keyboard, between rwin and rctrl).
I suppose you can assign another key, but it will have to be set up.

---

### Post by doncristobal on 2007-07-05
aaah... ça marche déjà mieux. 

Thank you for that hint. I tried with the right ctrl key (it does not work like the other ctrl key any more, e.g. ctrl-t for a new firefox tab, or ctrl-del to delete a whole word) and i can get â, ô, ó, ì, ú, ï etc.

But still, some things don't work: **spanish ~n*, greek &#953;', &#949;'** etc.**
???

*) For ~, i have to type alt gr-^
**) For á, i type rctrl, '/?/´, a

Isn't there a way to get the same behaviour as in window$? There, e.g. in greek, instead of the german ö (right from l), there is the always used accent ´: You simply type ´, then the vowel you want to stress, et voilà. with scim and m17n for greek, that key gives me a german ö, which, in greek, is of little use. 
It would be soooo convenient... :(

Any help is deeply appreciated!

---

### Post by doncristobal on 2007-07-05
With roman letters, i can now do whatever i want: ñ, ü, ï, ê, â, í, ù, etc... (Without a compose key!)

I just deactivated the "nodeadkeys" option in the Keyboard section of my xorg.conf: 

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ch"
#       Option          "XkbVariant"    "de_nodeadkeys"
EndSection

```

BUT: Greek accents still don't work: &#945;', '&#945;...

Does anybody have a hint for this problem? It's really impossible to write a greek text without accents, as almost every word needs one (however, it is always the same ascending accent, like the spanish acento or the french accent aigu).

---

### Post by bapoumba on 2007-07-06
I'm looking around. May be your font?
Edit: I could find it in the character map for FreeSans and FreeSerif: &#940;. Still looking to get it from the keyboard.

---

### Post by doncristobal on 2007-07-06
Bapoumba, tu n'arrêtes pas de m'aider... wow, merci beaucoup!

I have the impression that my fonts should be fine. I tried it in OpenOffice with several fonts, among them the open serif that [http://www.jw-stumpel.nl/stestu.html#T4.5](http://www.jw-stumpel.nl/stestu.html#T4.5) recommends. 

*Edit: In OpenOffices character map for freeserif, i find &#940; as U+03AC. *

Additionnally, i can display greek text with accents and copy-paste it to other programs, e.g.
> 
&#919; &#917;&#955;&#955;&#940;&#948;&#945; (&#945;&#961;&#967;&#945;&#912;&#950;&#959;&#965;&#963;&#945;: &#7961;&#955;&#955;&#940;&#962;, &#949;&#960;&#943;&#963;&#951;&#956;&#945;: &#917;&#955;&#955;&#951;&#957;&#953;&#954;&#942; &#916;&#951;&#956;&#959;&#954;&#961;&#945;&#964;&#943;&#945;), &#949;&#943;&#957;&#945;&#953; &#967;&#974;&#961;&#945; &#963;&#964;&#951;&#957; &#957;&#959;&#964;&#953;&#959;&#945;&#957;&#945;&#964;&#959;&#955;&#953;&#954;&#942; &#917;&#965;&#961;&#974;&#960;&#951;, &#963;&#964;&#959; &#957;&#959;&#964;&#953;&#972;&#964;&#949;&#961;&#959; &#940;&#954;&#961;&#959; &#964;&#951;&#962; &#914;&#945;&#955;&#954;&#945;&#957;&#953;&#954;&#942;&#962; &#967;&#949;&#961;&#963;&#959;&#957;&#942;&#963;&#959;&#965;, &#963;&#964;&#951;&#957; &#913;&#957;&#945;&#964;&#959;&#955;&#953;&#954;&#942; &#924;&#949;&#963;&#972;&#947;&#949;&#953;&#959;. &#931;&#965;&#957;&#959;&#961;&#949;&#973;&#949;&#953; &#963;&#964;&#951;&#957; &#958;&#951;&#961;&#940;, &#946;&#972;&#961;&#949;&#953;&#945; &#956;&#949; &#964;&#951;&#957; &#928;&#961;&#974;&#951;&#957; &#915;&#953;&#959;&#965;&#947;&#954;&#959;&#963;&#955;&#945;&#946;&#953;&#954;&#942; &#916;&#951;&#956;&#959;&#954;&#961;&#945;&#964;&#943;&#945; &#964;&#951;&#962; &#924;&#945;&#954;&#949;&#948;&#959;&#957;&#943;&#945;&#962; &#954;&#945;&#953; &#964;&#951;&#957; &#914;&#959;&#965;&#955;&#947;&#945;&#961;&#943;&#945;, &#963;&#964;&#945; &#946;&#959;&#961;&#949;&#953;&#959;&#948;&#965;&#964;&#953;&#954;&#940; &#956;&#949; &#964;&#951;&#957; &#913;&#955;&#946;&#945;&#957;&#943;&#945; &#954;&#945;&#953; &#963;&#964;&#945; &#946;&#959;&#961;&#949;&#953;&#959;&#945;&#957;&#945;&#964;&#959;&#955;&#953;&#954;&#940; &#956;&#949; &#964;&#951;&#957; &#932;&#959;&#965;&#961;&#954;&#943;&#945;. &#914;&#961;&#941;&#967;&#949;&#964;&#945;&#953; &#945;&#957;&#945;&#964;&#959;&#955;&#953;&#954;&#940; &#945;&#960;&#972; &#964;&#959; &#913;&#953;&#947;&#945;&#943;&#959; &#928;&#941;&#955;&#945;&#947;&#959;&#962;, &#963;&#964;&#945; &#948;&#965;&#964;&#953;&#954;&#940; &#954;&#945;&#953; &#957;&#972;&#964;&#953;&#945; &#945;&#960;&#972; &#964;&#959; &#921;&#972;&#957;&#953;&#959; &#954;&#945;&#953; &#945;&#960;&#972; &#964;&#951;&#957; &#924;&#949;&#963;&#972;&#947;&#949;&#953;&#959; &#920;&#940;&#955;&#945;&#963;&#963;&#945;. &#917;&#943;&#957;&#945;&#953; &#964;&#959; &#955;&#943;&#954;&#957;&#959; &#964;&#959;&#965; &#916;&#965;&#964;&#953;&#954;&#959;&#973; &#960;&#959;&#955;&#953;&#964;&#953;&#963;&#956;&#959;&#973;. &#919; &#917;&#955;&#955;&#940;&#948;&#945; &#941;&#967;&#949;&#953; &#956;&#953;&#945; &#956;&#945;&#954;&#961;&#940; &#954;&#945;&#953; &#960;&#955;&#959;&#973;&#963;&#953;&#945; &#953;&#963;&#964;&#959;&#961;&#943;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#959;&#960;&#959;&#943;&#945; &#940;&#963;&#954;&#951;&#963;&#949; &#956;&#949;&#947;&#940;&#955;&#951; &#960;&#959;&#955;&#953;&#964;&#953;&#963;&#956;&#953;&#954;&#942; &#949;&#960;&#943;&#948;&#961;&#945;&#963;&#951; &#963;&#949; &#964;&#961;&#949;&#953;&#962; &#951;&#960;&#949;&#943;&#961;&#959;&#965;&#962;.


Thank you everyone for any hint you can give me on this subject!

---

### Post by bapoumba on 2007-07-06
> **doncristobal said:**
> Bapoumba, tu n'arrêtes pas de m'aider... wow, merci beaucoup!
Pas de problème, et de rien.
That's funny, I was reading the exact same link you gave!
See section: 6.5.3 Classical Greek.

---

### Post by doncristobal on 2007-07-06
If i had known that it actually _was_ working! 

The only problem was that the acute accent &#900; was on the ; key, and i did not find it there, instead searching around '/?

> 
Accent 		key 	  result (on &#945;)
acutus (oxía) 		  ; 	    &#940;
gravis (varía) 		  ' 	    &#8048;
perispomenon (perispoméni) 		  [ 	    &#8118;
iota subscriptum (ypogegramméni) 		  ] 	    &#8115;
spiritus asper (dasía) 		  " 	    &#7937;
spiritus lenis (psíli) 		  : 	    &#7936;

(from [http://www.jw-stumpel.nl/stestu.html](http://www.jw-stumpel.nl/stestu.html), which seems to be very good resource in general)


So, for modern greek the accent problem is solved, as there is just this single accent &#900; on any vowel: &#915;&#949;&#953;&#940; &#963;&#959;&#965;, &#964;&#943; &#954;&#940;&#957;&#949;&#953;&#962;; - &#928;&#959;&#955;&#973; &#954;&#945;&#955;&#940;, &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974;.

:confused: but where do i find the question mark/semicolon ; ? (In the example, i switched to latin in order to get such a semicolon)

AHA! Found it myself: The semicolon/question mark is hidden under the Q key! 

:D [COLOR="Red"]So, for now, my languare input problems seem to be solved, MERCI BEAUCOUP A BAPOUMBA AND THANK YOU TO J. STUMPEL AND HIS [http://www.jw-stumpel.nl/stestu.html](http://www.jw-stumpel.nl/stestu.html) ):P

[/COLOR]I hope this thread can help other users, too. 
&#50504;&#45397; &#54616;&#49352;&#50836;
&#931;&#945;&#962; &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; &#960;&#940;&#961;&#945; &#960;&#959;&#955;&#973;!

&#935;&#961;&#953;&#963;&#964;&#972;&#966;&#959;&#961;&#959;&#962;

---

