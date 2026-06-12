---
title: "libreoffice"
date: 2013-10-28
forum: General Help
---

### Post by uaw1998@yahoo.com on 2013-10-28
I would like to do away with libreoffice and use openoffice insted.what is the best way to do this?

---

### Post by ping-wu on 2013-10-28
The easiest (and most straightforward) method for installing Apache OpenOffice is as follows:

sudo apt-get purge libreoffice*

goto [www.openoffice.org/download](www.openoffice.org/download) , click download, click on "open with Archive Manager", Ubuntu will download and decompress the packages into the en-US (or your own locale) folder

sudo dpkg -i en-US/DEBS/*.deb

sudo dpkg -i en-US/DEBS/desktop-integration/*.deb

---

### Post by uaw1998@yahoo.com on 2013-10-28
Thank you.

---

### Post by ajgreeny on 2013-10-28
> **uaw1998@yahoo.com said:**
> I would like to do away with libreoffice and use openoffice insted.what is the best way to do this?

I'm interested to know why you want to do this?  What do you find OOo does better than LO?

---

### Post by uaw1998@yahoo.com on 2013-10-28
open office works better for me.

---

### Post by ajgreeny on 2013-10-28
> **uaw1998@yahoo.com said:**
> open office works better for me.

Yes, that much I had supposed.

The question remains; in what way does OOo work better for you than LO?

---

### Post by David_Pecot on 2013-10-28
I was under the impression the LO is getting more active development and upgrades, whereas OOorg is just something else that Oracle inherited from Sun.

---

### Post by ajgreeny on 2013-10-29
> **David_Pecot said:**
> I was under the impression the LO is getting more active development and upgrades, whereas OOorg is just something else that Oracle inherited from Sun.

Yes, that is what I thought too, though I believe that OOo has begun to be a lot more active recently.

Personally I think I still prefer LO, but I admit I haven't seen OOo for a long time, and I am also using the most recent stable LO for 12.04.

---

### Post by ping-wu on 2013-10-29
We have switched all of our desktop/notebook machines from LO to Apache OpenOffice.  The main reason is that in LO, its Chinese UI was largely inadequate.  Equally important is that, when switched to Chinese locale, LO sometimes can become very sluggish, several times, we thought the system crashed.  The results are reproducible, not just flukes.  In comparison, the Chinese  translation of Apache OpenOffice was very professional done, and, so far, has been running very smoothly.

 Even in the English locale, we have found several glitches that made us feel uncomfortable about using LO.  For example, we couldn't change the program cache time (i.e., "Remove from memory after . . .") from the default value.  LO's page numbering became unstable when we use more than one page numbering layout (e.g., with table of contents one type of page numbering, then restarting page numbering in the main text body with another numbering type).  Both are regressions, but they occurred probably because LO was always in a development stage and it changes version numbers too frequently.

---

### Post by bapoumba on 2013-10-29
I'm still sticking with LO, although there is an annoying bug with the concordance file that makes indexes unusable. Using Apache OO just for that part when needed.

---

