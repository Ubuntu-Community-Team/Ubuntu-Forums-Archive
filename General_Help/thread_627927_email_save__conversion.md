---
title: "email save / conversion"
date: 2007-11-30
forum: General Help
---

### Post by kle on 2007-11-30
I have found several threads here about this topic, but nobody seems to have come up with a comfortable solution: 

Some of us need to save our day.-to-day  email in a format that can be viewed on various platforms. Doing so should require as little extra work as possible. The most universal formats would seem to be unformated text  and html. 

Apple mail will save all mail as text (automatic after first-time selection)
Thunderbird on all platforms has optional save as html (but the option has to be selected for each mail)

Evolution (on Kubuntu) and Kmail only seem to save as eml and kbox - respectively. No options given. 

My question: Surely it should be possible to convert a batch of saved kmails to html or text (with just the main headings and with the requested character encoding). There must be a scriot out there somewhere? Surely? 

A solution would be much apreciated.

---

### Post by kle on 2007-11-30
I forgot to add that one alternative way of saving cross-platform mail in Ubuntu is to use the print to PDF file alternative.  

In Gutsy the print to postscript printer seems to enabled by default. In some, but not all, programs run on Kubuntu you can check print to file. It requires more mouse-clicks than I am comfortable with, however, and PDF eats HD space fast.

---

### Post by HermanAB on 2007-11-30
Sortof, maybe...

You can install the fetchmail rpm and use formail to do some conversions, then pipe that into txt2html, txt2ps, ps2pdf and whatnot.  You would likely also require some sed and awk to remove some crud.

Good luck!

Herman

---

### Post by kle on 2007-12-01
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by kle on 2007-12-01
Why thank you! I shall certainly try that and let you know if it worked.

---

