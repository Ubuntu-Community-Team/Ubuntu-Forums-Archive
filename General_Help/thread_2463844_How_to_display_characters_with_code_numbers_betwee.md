---
title: "How to display characters with code numbers between 127 and 144"
date: 2021-06-19
forum: General Help
---

### Post by hakelm on 2021-06-19
If I insert characters with code numbers between 127 and 144 into an Open Office dokument I get the first row shown in the image below basically independent of what font I use.
I I paste the same characters  into the terminal using Windows 1252 font I get what is shown on the second line, utf-8 only results in a couple of boxes..
Encoding the same characters as HTML (&#<number>;) I get what is shown on the last line. 
Is there any way to find out what fonts would result in similar looks?


[ATTACH=CONFIG]288691[/ATTACH]

---

### Post by Impavidus on 2021-06-19
On Linux, we always use the Unicode character set nowadays, in UTF-8 encoding. Unicode copied the code points 128-143 (hexadecimal 80-9F) from the Latin-1 set, where those are control characters. That's why you got the boxes when pasting them in the terminal in UTF-8.

A web browser often assumes some text is in Windows-1252 encoding. There are so many mislabelled Windows-1252 html files around that that's the best assumption. So when you use the &#xxx; syntax, it will show the characters belonging to those numbers in Windows-1252, not in the normal Unicode encoding. There, they would be control characters and those wouldn't really make sense. For the characters not defined in Windows-1252 (like 0x81=d129), it substitutes a character from the webdings font.

In the second line of your output, it appears that all characters get separated by a Â. I don't know what's going on. Other than that, those are the Windows-1252 characters

The first line of your output shows the workaround people used in the 1990s. Back then, 7-bit ASCII was too limited and Unicode was very new, so people invented workarounds to get more characters. There were several 8-bit encodings (like Windows-1252 and Latin-1), but to get even more characters one could use a special font. One such font is [webdings](https://en.wikipedia.org/wiki/Webdings). It's really a dirty hack, so we don't do that any more. It mixes the encoding vector, linking the numeric IDs to the character names, with the glyph design, linking the character names to their appearance, which is a recipe for disaster whenever you change font, try to use a screen reader etc.

Unicode eliminates the need for such hacks, so all those weird characters now have a numeric ID of their own. The wiki page on webdings linked above shows their Unicode code points. Entering those numbers should give the right symbols in every font.

OpenOffice is apparently kind enough to assume you want the webdings symbols whenever you enter a character from the range 0x80-0x9f, and converts to the appropriate codepoints. A browser assumes you want the Windows-1252 encoding, and only if the code is undefined there will assume the webdings font. The terminal, when using utf-8, will simply assume these are control characters and you have some use for them.

But to answer your actual question: It's not about the fonts. Not since we abandoned that dirty hack with the webdings font. Every font should display about the same. It's just that some tools silently convert encodings.

---

### Post by hakelm on 2021-06-20
[COLOR=#000000]Thanks, I read your answer i the following way:
[/COLOR]The UTF-8 characters 0xC27F .. 0xC28F are listed as <control> and I assume the different or missing renderings of the UTF codes is up to the particular application.
[COLOR=#000000]Windows-1252 is an ASCII variant, so the [/COLOR]Â:s come from decoding the 1st byte, 0xC2, of the UTF-8 character.
H

---

### Post by Impavidus on 2021-06-20
Seems a plausible explanation for the Â: when the characters are encoded as UTF-8 and interpreted at Windows-1252, the 0xc2 bytes result in Â. I didn't quite catch how pasted the characters, but this makes sense.

You're correct (apart from a small slip in your hexadecimal numbers). The Unicode characters 0x80-0x9f, encoded as the 2-byte UTF-8 sequences 0xc280-0xc29f, are control characters. Some application use them as control characters, some assume you don't want those and substitute the Windows-1252 characters or, where those are undefined, the webdings characters, others substitute the webdings characters in all cases.

---

### Post by The Cog on 2021-06-20
Being pedantic, Windows-1252 is not an ASCII variant, it is one of many different extensions of ASCII. ASCII itself only defined 7-bit characters, 0x00-0x7f.

By my understanding, Linux uses Unicode throughout, encoded as UTF8.

Look for a Linux application called Character Map. I think it is installed by default on the Ubuntu desktop variants. It shows pretty-much all Unicode characters. You can double-click any of the characters in the tables and that puts them into a text field at the bottom where you can copy them for pasting into other windows. It also lets you show what those characters look like using different fonts (pull-down menu top left).

If you know the Unicode number for a character, you can enter it into other application text fields by starting with Ctrl-Shift-U and finishing with space or Enter. For example, the copyright symbol '©' is got by typing Ctrl-Shift-U, A, 9, Enter. That's how I just typed it into Firefox for this post. The Character Map app shows you the Unicode numbers, so you can use that to find and memorise your more commonly used characters.

---

### Post by Impavidus on 2021-06-20
Everything in Ubuntu uses Unicode in UTF-8. On Windows systems you may encounter Unicode in UTF-16. Files in different formats (all those 8-bit encodings like Windows-1252) may occasionally be encountered in the wild and tools still have some support for them.

To type strange characters I really prefer compose sequences, for those characters that have one defined. For example, © can be typed with compose, o, c. That's shorter than ctrl+shift+u, a, 9, enter and easier to memorise. But I don't think there're compose sequences for all of those webdings characters.

---

### Post by The Cog on 2021-06-20
I don't think I've ever seen a list of the composable characters and their sequences. So although I know they exist, I have never used them.

---

### Post by Impavidus on 2021-06-21
Try /usr/share/X11/locale/en_US.UTF-8/Compose. Those starting with <Multi_key> are the compose sequences. Characters composed using dead keys are also in that file. I don't know the details of how exactly it works and a few of those sequences don't appear to work on my system, so it may be that it isn't derived directly from that list. But most sequences work, if the required keys are present on my keyboard.

Usually I just guess.

---

### Post by The Cog on 2021-06-21
Oh wow! That's a whole can of worms I didn't know about. It's a good starting point. Thanks.

---

### Post by hakelm on 2021-06-21
You can also insert any UTF-8 character with these keystrokes shift-ctrl-u <code point in hex>
shift-ctrl-u 00a1 results in ¡ inverted exclamation mark

---

