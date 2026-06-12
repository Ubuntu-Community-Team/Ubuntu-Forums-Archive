---
title: "no non-latin characters showing up anymore in firefox"
date: 2005-08-10
forum: General Help
---

### Post by lonely on 2005-08-10
hello everybody.  :) 

No non-latin characters (cyrillic and arabic) showing up anymore in firefox.  :( 

When I open any site with non-latin text I get these &#1040;&#1053;&#1045; (cards like characters) instead of the cyrillic russian letters. (You may see it correctly on your own web browser).

I checked the font preferences in firefox but everything is ok. I tried anyway with "always use my fonts" with Unicode fonts selected, but still I see only cards-like characters in web pages.

I checked with a another browser (epiphany) and there is no such problem. But when I entered my password last time to launch Synaptic, it shows the card-like characters instead of the usual black points.

It might then be system page encoding problem.

Seems everything happened after installing java sdk (j2sdk1.4.2) and running a java front end for Bibtex (JabRef). But I can't see any connection.

Has anybody an idea ?

Thanks in advance.

(Ubuntu is really enjoyable. I've been using it for the last 3 weeks. Everything is working wondefuly : multilingual text editing, GIS mapping, audio and image editing.  :cool: )

---

### Post by lonely on 2005-08-10
Problem solved.

I had win font installed in ~/.fonts (not directly but by copying the ttf fonts in ~/.openoffice/1.1.3/user/fonts/). Having them removed, solved the problem.

;-) 

Hope that may help someone facing the same problem.

Ciao tutti.

---

