---
title: "alt character codes"
date: 2006-10-26
forum: General Help
---

### Post by markster23 on 2006-10-26
hi..  i'm new in linux and often need to use french accents in documents (for example in OO) like éêëèçàáâ ... in windows, there are codes you can use on your keyboard like ALT + 130 to produce the é symbol... i've noticed in linux, the alt codes do not work. is there any plans for support of this feature? im sure it would be quite appreciated by a lot of people.. it's a common annoyonance.. umm.. for now i'm using kcharselect, but it's time consuming and i'm so used to the alt codes in ms word... manually copying each accent to the clipboard and then pasting it is so un-natural when your typing a document.. is anybody aware of any plans to impliment or any shorter ways i can set it up to accept alt codes in ubuntu ?? thanks !!!

---

### Post by red_Marvin on 2006-10-26
I can input special characters by holding ctrl + shift and then typing a four digit hex value (0-9, a-f). It can't be ascii (only two hex digits) it must be unicode codes or something, but I think you can get those from kcharselect or something similar.

---

### Post by Brunellus on 2006-10-26
> **markster23 said:**
> hi..  i'm new in linux and often need to use french accents in documents (for example in OO) like éêëèçàáâ ... in windows, there are codes you can use on your keyboard like ALT + 130 to produce the é symbol... i've noticed in linux, the alt codes do not work. is there any plans for support of this feature? im sure it would be quite appreciated by a lot of people.. it's a common annoyonance.. umm.. for now i'm using kcharselect, but it's time consuming and i'm so used to the alt codes in ms word... manually copying each accent to the clipboard and then pasting it is so un-natural when your typing a document.. is anybody aware of any plans to impliment or any shorter ways i can set it up to accept alt codes in ubuntu ?? thanks !!!
the keycodes are in hex, not ASCII;  you should be able to enter them with CTRL + ALT + keycode in hex. 

There should be a character map with keycodes on it to help you.  Also, you could try changing the default language on your keyboard.  GNOME makes this pretty easy--I have mine set to change between EN-US/ EN-GB and ES

---

### Post by markster23 on 2006-10-26
that doesn't work for some reason.. ctrl + alt + E9, for example is supposed to give me é.. but it doesn't work, it actually switches windows, like alt + tab...  strange

> **Brunellus said:**
> the keycodes are in hex, not ASCII;  you should be able to enter them with CTRL + ALT + keycode in hex. 

There should be a character map with keycodes on it to help you.  Also, you could try changing the default language on your keyboard.  GNOME makes this pretty easy--I have mine set to change between EN-US/ EN-GB and ES

---

### Post by edd07 on 2006-12-02
You can enter the special characters with Ctrl + Shift + U, and then enter the code while still holding Ctrl + Shift

There's a thread about this: [http://ubuntuforums.org/showthread.php?t=288437&highlight=at+character](http://ubuntuforums.org/showthread.php?t=288437&highlight=at+character)

---

### Post by nidelius on 2009-04-29
you saved my day! Installed 9.04 with a strange letter in the password. Not so smart because when I booted I got only english keyboard in the login promt for some reason
ctrl + shift + u ftw

---

### Post by Kingsley on 2009-04-29
> **edd07 said:**
> You can enter the special characters with Ctrl + Shift + U, and then enter the code while still holding Ctrl + Shift

There's a thread about this: [http://ubuntuforums.org/showthread.php?t=288437&highlight=at+character](http://ubuntuforums.org/showthread.php?t=288437&highlight=at+character)
Nice. I was looking for something like this 2 years ago. Where can I get a list of the character codes?

---

### Post by VCoolio on 2009-04-29
You can find all unicode charts [here]("http://www.unicode.org/charts/"), so you can get all characters you want now!
Keep in mind that most fonts only support parts of unicode. The é å ç and stuff are common of course. You can check font-unicode compatability [here]("http://www.alanwood.net/unicode/fontsbyrange.html"); it is sorted by unicode charts and tells you what fonts support it.

For ß å é etc I would say using dead keys is best (set your keyboard layout). Also try right-alt combo's. For me for example, right-alt+w gives å and shift+right-alt+0 gives °. It depends on what key you have set as compose key.

---

### Post by Dhatri on 2010-01-04
I've tried using alt-shift-u on facebook, with no joy, I get as far as the Chinese looking character with I think numbers in the bottom right corners. I'm using ubuntu version 9.10.

---

### Post by edd07 on 2010-01-04
Are you sure you're entering the right code? Keep in mind it's Unicode, not ASCII. 

Or maybe the font used to render that text doesn't include thar character. Could you post a screenshot?

---

### Post by Dhatri on 2010-01-05
Aha! Unicode sorted it, thanks so much edd! Now added this to my bookmarks...

[http://ascii-table.com/unicode-search.php](http://ascii-table.com/unicode-search.php)

When putting a symbol in hold down Ctrl then shift, then press "u" one while still holding the first two...then type the code on the numeric keypad...

For example, to get &#2768; (OM)

type...

ctrl+shift+u, then release the u and type  0AD0

:P

---

### Post by piojunbabia on 2010-01-10
this is also a problem of mine, i just need to know it now and thank you for your posts...

---

### Post by AHrubik on 2010-03-08
I have confirmed Control+Shift+U works.

You will see the "U" entered into the field along with the code for the symbol you are trying to get but after correctly entering the code the enter text will revert to the symbol.

Unicode Character Chart:
[http://www.utf8-chartable.de/](http://www.utf8-chartable.de/)

Instructions repeated:

1. Hold Ctrl+Shift+U
2. Release U
3. Enter the code for the symbol you desire

Result should be the text you see converting into the symbol you desire. I had this issue and this solved my problem. Thank You!

---

### Post by piojunbabia on 2010-04-09
> **AHrubik said:**
> I have confirmed Control+Shift+U works.

You will see the "U" entered into the field along with the code for the symbol you are trying to get but after correctly entering the code the enter text will revert to the symbol.

Unicode Character Chart:
[http://www.utf8-chartable.de/](http://www.utf8-chartable.de/)

Instructions repeated:

1. Hold Ctrl+Shift+U
2. Release U
3. Enter the code for the symbol you desire

Result should be the text you see converting into the symbol you desire. I had this issue and this solved my problem. Thank You!
thank you, i figure this out also using the method you said.. thanks a lot...

---

### Post by GeoffreyTransom on 2013-04-23
Thanks to all who pointed bemused users in the right direction.

One thing I would say to folks who posted links for collections of unicode hexcodes though: the best resource for Unicode HEX codes is, well, **Unicode.org** - amirite? 

Within the unicode site, I use and recommend [THIS link]("http://www.unicode.org/charts/charindex.html") which unicode's searchable-by-name-**or-by-eyeball** page (the "by eyeball" bit is important). This is, to my way of thinking, a superior solution to the page cited by VCoolio (above, on P1 of the thread) which links to Unicode's **PDFs of code-sets** (with no ability to know ex ante which code is in which PDF). 

Not hatin' - just tryin to help.

Enjoy!

---

### Post by wildmanne39 on 2013-04-23
Thread closed. Please do not post in old threads.

---

