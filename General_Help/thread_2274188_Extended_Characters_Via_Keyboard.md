---
title: "Extended Characters Via Keyboard"
date: 2015-04-18
forum: General Help
---

### Post by Kurt_Alan on 2015-04-18
****

Besides English, I regularly type in Spanish and Haitien Kreyól.  I have created a doc from which I can copy/paste individual characters (as in Kreyól) but this is exceedingly slow.

This is the information I have gathered for doing same via keyboard but I can't get it to work. Using the example of **à ** can you tell me exactly what to input from my keyboard?

Kreyòl

ò
à    &#xE0;     hex
è

Notes:

You can use Ctrl+Shift+u followed by the code in hex. 

You only need to hold down Ctrl and Shift while typing the code

---

### Post by Impavidus on 2015-04-18
Several possibilities.

Choose a keyboard layout that directly supports all characters you often need, either via a third level chooser or dead accent keys.
OR
Use ctrl+shift+u, hex code. Find the hex codes in a unicode table ([http://en.wikipedia.org/wiki/Latin_script_in_Unicode](http://en.wikipedia.org/wiki/Latin_script_in_Unicode)) and learn them all by heart. You can either hold ctrl+shift when typing the hex code, or release them before and terminate the hex code with space, enter or another ctrl+shift+u, hex code.
OR
Configure a compose key and type additional characters using compose, some sequence (compose sequences are far easier to memorise than hex codes).

I prefer the compose key, which supports most characters in latin script, although not all. I sometimes have to type ctrl+shift+u 2 3 7 ctrl+shift+u 3 0 1 space just to type &#567;&#769;, a character you actually need in dutch, although it's not present in unicode. Most people just ignore that accent.

---

### Post by dave0109 on 2015-04-18
I have a similar requirement, in that I type a lot in Spanish as well.  Whilst I can remember the character codes for ¡ ¿ and ñ, it's very tedious to type that way.  So I went down the route of modifying the keyboard layout file and changing the key mappings to do what I want by using the AltGr modifier.  You should be able to do something similar for Spanish at least, if not for Kreyól - it all depends on how many accented characters you need.

Because I'm in the UK and using a UK layout keyboard, I edited the file in /usr/share/X11/xkb/symbols/gb.  You'll need to pick whichever you're using as a base.  A few years back, I would create my own completely new layout, but these days, for me, the "English (UK, extended WinKeys)" already has most of what I want.  In there, I simply add lines for the characters I used above...

```

key <AE01> { [     1,          exclam,      exclamdown,    NoSymbol ] };
key <AB06> { [   n,                 N,          ntilde,      Ntilde ] };
key <AB10> { [ slash,        question,   questiondown, questiondown ] };

```

Then logging out and back in and/or reselecting the keyboard layout, will pick up the changes.  So now, in order to enter an 'ñ' I simply press AltGr-n. The only character I don't have is the u with umlaut, but I use such words so infrequently, that I don't find that I miss having a short-cut.

The only down side to this is that very often a software update or version update will reset that file, and I have to do the whole thing again, but overall, the time that it saves is vast.

---

### Post by Kurt_Alan on 2015-05-09
> **Impavidus said:**
> Several possibilities.

Choose a keyboard layout that directly supports all characters you often need, either via a third level chooser or dead accent keys.
OR
Use ctrl+shift+u, hex code. Find the hex codes in a unicode table ([http://en.wikipedia.org/wiki/Latin_script_in_Unicode](http://en.wikipedia.org/wiki/Latin_script_in_Unicode)) and learn them all by heart. You can either hold ctrl+shift when typing the hex code, or release them before and terminate the hex code with space, enter or another ctrl+shift+u, hex code.
OR
Configure a compose key and type additional characters using compose, some sequence (compose sequences are far easier to memorise than hex codes).

I prefer the compose key, which supports most characters in latin script, although not all. I sometimes have to type ctrl+shift+u 2 3 7 ctrl+shift+u 3 0 1 space just to type &#567;&#769;, a character you actually need in dutch, although it's not present in unicode. Most people just ignore that accent.


@impavidus --

Thank you for this.  I find that using shift + ctrl + u + four character hex involves about as many steps as a copy/paste of the desired letter from a list.

However, I'm trying this: On my wall I made a chart titled: ctrl + shift +u00

Then I just make a short list as follows:

ò      f2
è      e8     etc.

Maybe in time I'll speed up!

---

