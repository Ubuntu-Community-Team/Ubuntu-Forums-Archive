---
title: "Collecting Data From Wikipedia Pages"
date: 2013-12-31
forum: General Help
---

### Post by MFI-Spencer on 2013-12-31
I'm trying to collect data from Wikipedia that can be updated for a database/calculator, but I have only used GUI based scripting tools such as AutoHotKey for this type of collection in the past. I would like to use a program or command line tool and am not sure where to start.

---

### Post by tgalati4 on 2013-12-31
```
man wget
man curl
```

Include some specifics (like the page and info you are trying to collect--but not bitcoin-related) and you may get more help.

---

### Post by oldos2er on 2013-12-31
See [https://en.wikipedia.org/wiki/Wikipedia:Database_download](https://en.wikipedia.org/wiki/Wikipedia:Database_download)

Torrenting would be best.

---

### Post by MFI-Spencer on 2014-01-02
I am building a list of metals/materials and their uses. I want to have a database that will pull up the correct metal for an application allowing for the user to type in any part of the information they have such as: machinability, SAE grade, general use, alloy content, UNS, ASTM, or ISO numbers. I would like to in the future extend it to have heat treat information and other specific properties of the metals allowing someone find the metal they need for their job, then find other information like how much it will weigh at any given length.

I have started printing out the information have and entering it by hand, but this method is prone to errors and very slow.

Pages with some of the information I have pulled:

[http://en.wikipedia.org/wiki/Brass](http://en.wikipedia.org/wiki/Brass)
[http://en.wikipedia.org/wiki/List_of_copper_alloys](http://en.wikipedia.org/wiki/List_of_copper_alloys)
[http://en.wikipedia.org/wiki/SAE_steel_grades](http://en.wikipedia.org/wiki/SAE_steel_grades)
[http://en.wikipedia.org/wiki/Unified_numbering_system](http://en.wikipedia.org/wiki/Unified_numbering_system)
[http://en.wikipedia.org/wiki/Steel_grades](http://en.wikipedia.org/wiki/Steel_grades)
[http://en.wikipedia.org/wiki/ASTM_International](http://en.wikipedia.org/wiki/ASTM_International)
[http://en.wikipedia.org/wiki/Steel_grades](http://en.wikipedia.org/wiki/Steel_grades)

I also tried copy and past to excel, but the format never seems to come out right. I'll take any suggestions, like I said I am typing this stuff into excel by hand right now.

---

### Post by amanchesterman on 2014-01-02
"I also tried copy and past to excel, but the format never seems to come out right."

This is just a guess, but I wonder if that's because you are copying the text from a web page, which has html formatting tags in it (e.g. for the links to other Wikipedia pages), and when you paste them into Excel they mess up the layout?
A simple thing you could try is to copy the text from the Wikipedia page and paste it first into a simple text editor. I use Leafpad, which comes with Xubuntu, but you may have something different. The main thing is you want it to accept 'plain text' only, since that will strip out all the web page formatting. Then copy and paste **that** text into Excel and see if it's any better.

Good luck!

---

### Post by tgalati4 on 2014-01-02
In school, I used a much older copy of this handbook:  [http://www.amazon.com/Eshbachs-Handbook-Engineering-Fundamentals-Myer/dp/0470085789](http://www.amazon.com/Eshbachs-Handbook-Engineering-Fundamentals-Myer/dp/0470085789)

It's format is also a hodge-podge of formats because of all of the different sources of information used.

This project is trying to unify metal fabrication:  [http://opensourceecology.org/wiki/Basic_Fabrication_Skills](http://opensourceecology.org/wiki/Basic_Fabrication_Skills)

---

### Post by bapoumba on 2014-01-02
> **amanchesterman said:**
> "I also tried copy and past to excel, but the format never seems to come out right."

This is just a guess, but I wonder if that's because you are copying the text from a web page, which has html formatting tags in it (e.g. for the links to other Wikipedia pages), and when you paste them into Excel they mess up the layout?
A simple thing you could try is to copy the text from the Wikipedia page and paste it first into a simple text editor. I use Leafpad, which comes with Xubuntu, but you may have something different. The main thing is you want it to accept 'plain text' only, since that will strip out all the web page formatting. Then copy and paste **that** text into Excel and see if it's any better.

Good luck!

ctrl-shift-v (or paste special from the menu) > choose "unformatted text".

---

