---
title: "Possible UTF Issue"
date: 2008-01-23
forum: General Help
---

### Post by podollb on 2008-01-23
Hi use Ubuntu at work and everything works great and I have hardly any complaints, but I do have one weird thing that I need help with. I use Eclipse (for Java development) and we have header comments with a copyright symbol in the text. On other peoples machines the files show up as the real copyright symbol (the "c" with the circle around it) but on my box it shows as a "?" mark type symbol. BUT I can cut and paste a copyright symbol out of a webpage or whatever and paste it over my "?" thing and it displays just fine. So what would cause the encoded symbol that is the copyright which everyone else sees just fine break for me?

---

### Post by podollb on 2008-01-23
Most developers use Windows [where I work] and one of them (a long time ago) put the copyright comment as a header to all our files. Which was no big deal and seemed to display the copyright symbol just fine (on their Windows machines), but...

Here is what the headers look like [on my Ubuntu 7.10 linux box] once I grab files from CVS:
> Copyright &#65533; 2004, 2008

It looks fine in Window:
> Copyright © 2004, 2008

Interestingly, if I cut and paste the copyright symbol from above (or from some website that properly displays it) I can paste it into my flie and it displays fine...

So it is confusing, either the character encoding doesn't recognize the format it's stored in (in the actual file) or can it vary? And why can I properly see it if I cut and paste, is that a different encoding? I am confused. I can give anyone all my systems locale information if they want...

---

