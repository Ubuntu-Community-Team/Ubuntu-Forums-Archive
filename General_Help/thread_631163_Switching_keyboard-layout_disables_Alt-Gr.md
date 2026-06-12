---
title: "Switching keyboard-layout disables Alt-Gr"
date: 2007-12-04
forum: General Help
---

### Post by Zerothi on 2007-12-04
Hi all

I have a serious headache problem..

I discovered the Dvorak keyboard layout on the internet and so decided to try it out!!

After doing some search on the internet i found my prayers!

Because i am danish i had to do it al from scratch!!

So i created my own dvorak keyboard-layout in

/usr/share/X11/xkb/symbols

named "dkdvorak" and setting the keys up for the right layout!

And then this works perfectly!! Even Alt-Gr-7 which makes me and braceleft "{"...

But heres my problem!!

My normal setting in

/etc/X11/xorg.conf

is

Option		"XkbLayout"	"dk(basic)"

and all keys work! Even Alt-Gr-7 which makes me and braceleft "{"...
But i want to be able to switch easily between the qwerty-layout and the dvorak-layout, so i added/replaced the following lines in /etc/X11/xorg.conf

Option		"XkbLayout"	"dk(basic),dkdvorak(dvorak)"
Option		"XkbOptions"	"grp:switch,grp:alt_shift_toggle"

The last line enables me to switch between the layouts by pressing "Alt-Shift".
And the switching in itself works aswell, but depending on which layout is written first, in this case "dk(basic)", that layout cannot use Alt-Gr-7 "{".

Only the last, in this case "dkdvorak(dvorak)".

Is there a way to bypass this error?

Thanks

---

### Post by jakommo on 2007-12-04
Hi Zerothi,

what is your value for Option "XkbModel" in xorg.conf?
for me (qwertz DE) it has to be Option "XkbModel"   "pc105".
if I user e.g. "pc104" AltGr stops working.
maybe that helps.

---

### Post by Zerothi on 2007-12-05
Sry should have stated that in my first post... But it is pc105...
It's standard for danish keyboards.. But when i switch it does not change it to anything else right? Or else that could be the case... But it's just odd, cause it's the last option in Layout that works with Alg-Gr!!!

Very strange... Any idea?

---

### Post by metalheart on 2007-12-05
Looks like reinventing the wheel

[http://www.danskdvorak.dk/](http://www.danskdvorak.dk/)

---

### Post by Zerothi on 2007-12-05
I know [http://www.danskdvorak.dk/](http://www.danskdvorak.dk/)... And no it does not help... In fact i am helping them with the layout of the Dvorak system for Linux... They DONT have a description on setting dvorak up on Linux-stations... And as i remarked... It has nothing to do with setting up another keyboard-layout, it's only a matter of: 
"What goes wrong when switching between layouts?"

So no reinventing the wheel.

---

