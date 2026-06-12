---
title: "Does Libre Office have its own distinct set of fonts?"
date: 2013-02-21
forum: General Help
---

### Post by Paddy Landau on 2013-02-21
I am having a perplexing time.

I wish to put a certain character into a document.

Looking through the Character Map, I find the character that I need in the Webdings font.

But when I attempt to put this into my Libre Office document, it puts in a different character.

Screenshot 1: Character Map showing Wingding's first 77 characters (A–Z, a–z, and more). The aeroplane, which you can see is Ò or Unicode 00D2, is highlighted.
[attach]231722[/attach]

Screenshot 2: Libre Office with the letters A, Z, a, z, å (Unicode AA) and Ò (Unicode D2).
[attach]231723[/attach]

As you can see, the letters A, Z, a and z all match. But the Unicode characters AA and D2 do not; they show respectively a radio and an aeroplane in Character Map, but a folded piece of paper and an in-tray in Libre Office.

In fact, I cannot find the folded piece of paper or the in-tray anywhere in Character Map. From where is Libre Office getting them?

Please help me resolve this discrepancy so that I can find the characters that I need in Libre Office.

[LIST]
[*]Ubuntu 12.04 64-bit fully updated.
[*]Libre Office 4.0.0.3
[/LIST]

---

### Post by vasa1 on 2013-02-21
Re. LibreOffice fonts, I see this in **3.6**:

---

### Post by The Cog on 2013-02-21
What character are you actually trying to put into LO? 

I'm on Xubuntu 12.10. In Character Map, those two characters actually show up as accented letters whcih is what the description below says they are. However, when I paste them into LO, I see the little a and O acute if I use most fonts and I see the paper and in-tray if I change the font to webdings.

So there seems a disparity between LO+webdings and Character Map. And Character Map behaves differently between 12.04 and 12.10.

There is a unicode plane symbol at U+2708 that works in most fonts.

---

### Post by Paddy Landau on 2013-02-21
> **vasa1 said:**
> Re. LibreOffice fonts, I see this in **3.6**:
I also have the Liberation fonts.

> **The Cog said:**
> What character are you actually trying to put into LO?
I was trying to add the five-point star, noted in Character Map as Unicode F2 (ò). In Libre Office, I get something that looks like a squirrel.

> **The Cog said:**
> So there seems a disparity between LO+webdings and Character Map. And Character Map behaves differently between 12.04 and 12.10.
Indeed. Most frustrating. I also tried to use Specimen Font Viewer, and that gives the same result as Character Map.

I think that I should post a query on the Libre Office mailing list.

** EDIT:** I have [posted this question]("http://nabble.documentfoundation.org/Does-Libre-Office-have-its-own-distinct-set-of-fonts-td4039236.html") to the Libre Office mailing list.

---

### Post by The Cog on 2013-02-21
Can I suggest that you forget dingbats and use 2605 Black Star instead?
Although I am very keen to know why dingbats behaves so oddly this way. I will follow that question with interest.

---

### Post by Paddy Landau on 2013-02-21
> **The Cog said:**
> … forget dingbats and use 2605 Black Star instead?
That's a good workaround, thank you.

---

### Post by The Cog on 2013-02-21
I just discovered that in my LO, capital 'H' comes out as a black star in dingbats. So if you really want to use dingbats, try that.

---

### Post by Paddy Landau on 2013-02-21
> **The Cog said:**
> I just discovered that in my LO, capital 'H' comes out as a black star in dingbats. So if you really want to use dingbats, try that.
That's strange. It seems that Dingbats is doing something similar to Webdings. Curiouser and curiouser!

---

### Post by The Cog on 2013-02-21
Neither webdings or dingbats conform to unicode - I think they were invented to solve a problem that unicode eventually solved, so I would regard them as legacy fonts now. I would always prefer to use a proper unicode character if I could find one.

---

### Post by Paddy Landau on 2013-02-21
> **The Cog said:**
> … I would regard them as legacy fonts now. I would always prefer to use a proper unicode character if I could find one.
Thank you. That makes sense. It does mean, however, that you would have to use images instead of fonts for certain characters. Fortunately, that is quite easy with Libre Office.

I shall bear this in mind next time.

---

### Post by Paddy Landau on 2013-02-22
The resolution to this problem (see the [Libre Office thread]("http://nabble.documentfoundation.org/Does-Libre-Office-have-its-own-distinct-set-of-fonts-tp4039236.html")) seems to be that Webdings is unreliable, and I should rather use an image.

It is not a perfect solution, and still leaves questions unanswered, but it is at least a reliable solution.

I shall mark this thread as solved even though the original question is unanswered.

---

### Post by Paddy Landau on 2013-02-22
We have a solution. Don't look for the character in Character Map. Instead, look for the character in the menu Insert > Special Character.

Doing this shows that Webdings in Libre Office is identical to Webdings in Windows, not Ubuntu.

Thinking about it, I've just realised that this makes sense — you wouldn't want a document to change in appearance just because you moved it from Windows to Ubuntu to Mac. Although how Libre Office does this is a mystery to me!

---

### Post by The Cog on 2013-02-22
> Insert > Special Character.Ooh, that's an interesting one. I had not even noticed its existence. A new toy to play with. 
Notice that Insert Special shows a unicode value. Apart from webdings, Insert Special and Character Map appear to agree on the appearance of characters (on a cursory inspection).

---

