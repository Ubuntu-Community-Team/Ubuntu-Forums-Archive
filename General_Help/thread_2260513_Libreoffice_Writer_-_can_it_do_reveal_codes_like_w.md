---
title: "Libreoffice Writer - can it do reveal codes like word perfect?"
date: 2015-01-12
forum: General Help
---

### Post by Tom_Carr on 2015-01-12
I have done some googleing and find lots of questions and requests for libreoffice writer to do reveal codes like word perfect, but I can't find any solution.  
Does this option exist in any form?  Is there an add on that will do it?

---

### Post by dragonfly41 on 2015-01-12
It appears that Word Perfect is unique in providing this feature ..

see last column .. Reveal Codes .. under Characteristics section here ..

[http://en.wikipedia.org/wiki/Comparison_of_word_processors](http://en.wikipedia.org/wiki/Comparison_of_word_processors)

---

### Post by Impavidus on 2015-01-12
I don't think WP is really unique in that feature. If you move over to the TeX world, you'll always have codes available. Depending on whether you use a high level front end or not (I don't), it may not even be possible to hide the codes.

In that wiki page, it doesn't say "no" on any row of that last column.

---

### Post by dragonfly41 on 2015-01-12
o.k. then .. regarding LibreOffice Writer .. this suggests no ..

[http://ask.libreoffice.org/en/question/43071/does-libreoffice-have-a-reveal-codes-functionality-like-wordperfect/](http://ask.libreoffice.org/en/question/43071/does-libreoffice-have-a-reveal-codes-functionality-like-wordperfect/)

---

### Post by Holger_Gehrke on 2015-01-12
> **Tom_Carr said:**
> I have done some googleing and find lots of questions and requests for libreoffice writer to do reveal codes like word perfect, but I can't find any solution.  
Does this option exist in any form?  Is there an add on that will do it?

The answer is "no" and "yes, in a certain way". It's not something you can do in {Star|Open|Libre}Office, but the od? file are actually nothing but zip files full of XML. So you can just unzip an od? and work directly with the XML. The format is documented at 'https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=office'.

The feature has been requested and voted on several times, there even was a proof-of-concept implementation as a macro written in 2004, but nothing happened because -- basically -- neither the companies that finance some of the development nor any of the independent hackers working on the programs are interested.

---

### Post by ski_phreak on 2015-06-20
I did a T.V. repair for Bruce Bastian (co-founder of WordPerfect) back 7-8 years ago.  Before we trotted his TV out to the van, I asked him  if WP had patented the daylights out of the "reveal code" idea.  Bearing in mind that he's not a patent attorney, he said "As far as I know, that's one thing that never got patented."

I wonder why nobody (other than LaTeX, of course) does it?  Seems so critical to those who grew up with it.  How many hours have we lost trying to figure out where our formatting got all fouled up--and how to fix it.

---

