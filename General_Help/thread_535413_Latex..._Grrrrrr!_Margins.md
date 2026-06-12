---
title: "Latex... Grrrrrr! Margins"
date: 2007-08-26
forum: General Help
---

### Post by RudolfMDLT on 2007-08-26
Hi there,

I need help with Latex! My Professor sets limits on reports on the number of pages to be handed in. This is great because, by minipulating the margins in a WYSIWYG editor you get about a thousand more words at least! 

Using Latex I'm a little buggered here as latex only uses 1/3 of the page surface area!

I have done some google homework and on the forums and have found some code that is supposed to work... but doesn't.

Can someone please tell me how you would get LaTeX to produce a PDF document with the text 3cm (about 1 inch) from the left side of the page, 3 cm from the right, top and bottom. and form there I'll modify it! I have really been strugeling with this for a LONG time!  

Thanks for the help guys!

Rudolf

---

### Post by tzulberti on 2007-08-26
This might work:
\usepackage[top=1.5cm, bottom=1.5cm, left=1cm, right=1.5cm]{geometry}

---

### Post by mali2297 on 2007-08-27
You can also manipulate the margins with \addtolength:

```

\addtolength{\hoffset}{-1.5cm}
\addtolength{\textwidth}{3cm}
\addtolength{\voffset}{-2cm}
\addtolength{\textheight}{4cm}

```

I usually experiment with these settings until they come to my liking.

---

### Post by RudolfMDLT on 2007-09-15
> **tzulberti said:**
> This might work:
\usepackage[top=1.5cm, bottom=1.5cm, left=1cm, right=1.5cm]{geometry}

It did! thank you very much! :)

---

