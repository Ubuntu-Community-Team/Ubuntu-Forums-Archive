---
title: "Emojis not showing correctly"
date: 2019-07-28
forum: General Help
---

### Post by lo-scrondo on 2019-07-28
This is my first time here, so I hope I'm in the correct place.

I've noticed that on my freshly installed (and updated) Ubuntu 19.04 the numerical emojis (from 0 to 9) are lacking.
Such malfunction appears in *every* application, so I thought it was a problem of the Noto Emoji Fonts - but on Ubuntu 18.04 every emoji is working correctly and trying to update with
```
sudo apt install fonts-noto-color-emoji
```
did not fix the problem.

PS: you could see if your system is interested too by the problem looking at [https://getemoji.com/](https://getemoji.com/) : in the "Symbol" category look to the numbers row - there you could see if all numbers (from 1 to 10) have the same style (i.e. white text with blue background) or not.

---

### Post by lo-scrondo on 2019-07-28
Just installed Disco Dingo on another two machines - the bug persists. Maybe I'll have to report this bug?

---

### Post by Holger_Gehrke on 2019-07-29
I'm on XUbuntu 18.04 and see black and white keycaps instead of a blue background for the digits from 0 to 9 on the page you link to. The 'FREE' button before and the '10' button after the digits have a blue background and the font of the digits is different from the '10'. So it's not **just** the Ubuntu version. Could it be that you have a (very) old version of Firefox on the machine with 18.04 ? FF uses it's own font for emoji in /usr/lib/firefox/fonts/ (TwemojiMozilla.ttf on Firefox 68). This was changed in the last one or two years. Just like on your machines using 19.04, installing the Noto Color Emoji does **not** change a thing on my machine.
These Symbols are actually **meant** to be keycaps and are complex things according to [https://www.unicode.org/emoji/charts/emoji-list.html](https://www.unicode.org/emoji/charts/emoji-list.html). They are made up of the code for the digit (0030 to 0039), a combinator (fe0f) and the background (20e3). Using ctrl-shift-u to enter these codes in a browser text entry field gets me a black and white keycap symbol (here, have one: 1&#65039;&#8419; ). The same in Libre Office Writer. BUT if I enter the same combination in the xfce4-terminal or in mousepad (a simple texteditor) or in bluefish (a more complex editor aimed at web-development) or in the text-tool in gimp I get a bevelled blue keycap. So it's not the system, it's program specific or a problem in a library these programs have in common.

Holger

---

### Post by lo-scrondo on 2019-08-10
> **Holger_Gehrke said:**
> BUT if I enter the same combination in the xfce4-terminal or in mousepad (a simple texteditor) or in bluefish (a more complex editor aimed at web-development) or in the text-tool in gimp I get a bevelled blue keycap. So it's not the system, it's program specific or a problem in a library these programs have in common.

Holger

Thank you for interesting in the issue!

In fact, I use emojis mainly in Nautilus (to get a huge mass of pdfs organized)...in Ubuntu 18.04 the keycaps emojis worked correctly, but in 19.04 they do not...

---

