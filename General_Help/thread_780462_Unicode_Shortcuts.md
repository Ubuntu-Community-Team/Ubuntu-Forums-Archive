---
title: "Unicode Shortcuts"
date: 2008-05-03
forum: General Help
---

### Post by BobSongs on 2008-05-03
Would anyone have a quick shortcut for the unicode keys that I've grown accustomed to in Windows? (Note: this is **not** a "Windows is better than Ubuntu" post.)

What I mean: in Windows one holds down the left **Alt** key and then types a series of numbers in the **numeric keypad**. This produces a number of handy symbols. Alt+0151 produces the "m-dash" (—), Alt+0147 = open quotes (“), Alt+0148 = close quotes (”).

The GNOME Character Map (Applications > Accessories > Character Map) does have these characters. I'm not asking for a tour of that applet as much as I'd like to know if someone has figured out if it is possible to produce these symbols through simple keystrokes, it is done in Windows.

The Character Map shows the Unicode when a character is selected, such as "U+2014" is associated with "m-dash", "U-201C" with open quotes and U+201D with close quotes. Obviously holding down the "U" key in conjunction with these figures does nothing.

Just wondering if anyone has unraveled this mystery. I am obviously a Windows expatriot (spelling corrected, thanks **peyre**). And those shortcuts have proven valuable.

Using the Character Map is an alternative... but I'm hoping someone can unravel the Unicode shortcut mystery.

----------------

**Solution (tyvm shirilover):**

To create a Unicode symbol, start with the Character Map (Applications > Accessories > Character Map).

Locate a commonly used symbol and take note of the Unicode sequence. In this case the © symbol (*copyright*, Unicode [COLOR=DarkRed]**00A9**[/COLOR]) and use the following steps:

[LIST]
[*]While holding down [COLOR=Navy]**Ctrl**[/COLOR] and [COLOR=Navy]**Shift**[/COLOR], hit the [COLOR=DarkGreen]**U**[/COLOR] key (now an underlined **_u_** appears)
[*]Let go of all keys
[*]Type the [COLOR=DarkRed]**00A9**[/COLOR] Unicode sequence (now the screen shows an underlined **_u00A9_**)
[*]Hit the Space Bar **or** Enter key and the Unicode symbol © appears.
[/LIST]
Excellent—this is what I was hoping for.
 
So for those reading through this post sometime in the future, here's the equivalents for what I requested:[INDENT]2014 = — (m-dash)
201C = “
201D = ”
2018 = ‘
2019 = ’
00BC = ¼
00BD = ½
00BE = ¾
00A9 = ©
00AE = ®
00D7 = ×
00F7 = ÷
2666 = [SIZE=3][COLOR=Red]&#9830;[/COLOR][/SIZE]
2665 = [SIZE=3][COLOR=Red]&#9829;[/COLOR][/SIZE] 
2663 = [SIZE=3]&#9827;[/SIZE]
2660 = [SIZE=3]&#9824;[/SIZE]
2669 = [SIZE=3]&#9833;[/SIZE]
266A = [SIZE=3]&#9834;[/SIZE]
266B = [SIZE=3]&#9835;[/SIZE]
266C = [SIZE=3]&#9836;[/SIZE]

[/INDENT]Fully functional. Refer to the Gnome Character Map for more symbols. The Unicode appears at the bottom left of the Character Map box as you click each symbol.

---

### Post by BobSongs on 2008-05-04
*bump*

---

### Post by shirilover on 2008-05-04
Alt-key combos can be replaced with Ctrl+Shift+U+hexcode, while holding down both Ctrl and Shift.

---

### Post by BobSongs on 2008-05-07
> **shirilover said:**
> Alt-key combos can be replaced with Ctrl+Shift+U+hexcode, while holding down both Ctrl and Shift.
Excellent!

This is how it works.

To create the &#8800; symbol (Not Equal To, Unicode [COLOR=DarkRed]**2260**[/COLOR]) I'd use the following steps:

[LIST]
[*]While holding down **Ctrl** and **Shift**, hit the **U** key (now an underlined **_u_** appears)
[*]Let go of all keys
[*]Type the [COLOR=DarkRed]**2260**[/COLOR] Unicode sequence (now the screen shows an underlined **_u2260_**)
[*]Hit the Space Bar **or** Enter key and the Unicode symbol **&#8800;** appears.
[/LIST]
Excellent&#8212;this is what I was hoping for.
 
So for those reading through this post sometime in the future, here's the equivalents for what I requested:[INDENT]2014 = m-dash = &#8212;
201C = open double quotes = &#8220;
201D = close double quotes = &#8221;
2018 = open single quote = &#8216;
2019 = close single quote = &#8217; = apostrophe
[/INDENT]Fully functional.

---

### Post by Luis Fernando Sarmiento on 2008-08-10
Nice explanation, Bob. This is the level of clarity needed!

---

### Post by simosx on 2008-08-30
Here is a list of ways to type special characters in Linux,
[http://blogs.gnome.org/simos/2008/02/03/typing-squiggles-and-dots-in-gnome-and-gtk-applications/](http://blogs.gnome.org/simos/2008/02/03/typing-squiggles-and-dots-in-gnome-and-gtk-applications/)

An additional way to type special characters is to use mnemonics and the "Compose" key.

---

### Post by peyre on 2009-09-22
That's great, BobSongs!  I'm going to use that method myself, once I can find a list of the unicode symbols that actually matches what comes up when I type the codes (I've found some lists, but when I type in what one list says is the unicode for a given symbol, Xubuntu returns a different character).

btw, I think you meant you're a Windows expatriate (meaning your "home" isn't in Windows any more) rather than an ex-patriot (meaning no longer loyal to Microsoft).

---

### Post by BobSongs on 2009-11-25
lol

Sorry to take so long to answer; and yes: I'm a Windows expatriate. I confess I started using Windows at version 3.0 when an office co-worker looked at my install (during the DOS days) and said: "Windows, hmm? Yeah; I heard about this. This is gonna seriously fail."

I used Win from 3.0, 3.1, 3.11wfw, 95a, 95b, 98, 98SE, Me, 2000 Pro and XP thru to SP3. In 2005 I asked a friend if there was a Linux out there that "Grandma could use". He recommended Ubuntu. I tried version 5.04 (Hoary Hedgehog) and it was miserable. Talk about not answering my question. Then six months saw the release of Breezy Badger. I gave Ubuntu another try. Soon I was using Ubuntu far more than XP. Now Windows has been put to rest once and for all. There are times when I miss a certain functionality. But overall, I'm pleased with the change.

The best moment came when my daughter walked into the room and said: "Dad? I've been using Windows XP where I babysit... will you promise never to put it back on our computer?" I laughed and said: "That's easy enough to comply with. It's not coming back." She gave me a hug and thanked me.

I used to re-install Windows on a regular basis. I'm talking ... sometimes a twice a day if things went horribly wrong. But usually once every 3 weeks. Ubuntu sees a re-install ... every six months. I don't miss the regular re-installations. Not to mention the stack of XP driver CDs and the tweaking and ... ugh.

---

### Post by clanmackay on 2010-08-01
> **BobSongs said:**
> Excellent!

This is how it works&#8230;


Lovely.  Thank you.

---

### Post by jamalpp786 on 2012-09-02
another way install the package "unicode" by "sudo apt-get install unicode". then type "unicode" in terminal

---

### Post by SantaFe on 2012-09-02
In case anyone's looking for a full list of Unicodes, there's one here: [http://en.wikipedia.org/wiki/List_of_Unicode_characters](http://en.wikipedia.org/wiki/List_of_Unicode_characters)¡

---

### Post by wildmanne39 on 2012-09-02
Thanks for sharing. Thread Closed.

---

