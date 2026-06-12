---
title: "Gaim 2.0 beta 4 xml parser error when ./configure"
date: 2006-10-25
forum: General Help
---

### Post by DigitalDuality on 2006-10-25
i'm attempting to install the latest gaim, and guifications.

I uninstalled beta 3 all together and i remember having a tremendous time getting that installed, and yet again i'm having problems with beta 4.

during the 
sh ./configure

i get this error and it just quits

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

the make file isn't created so i can't go any further

Help?

---

### Post by DigitalDuality on 2006-10-25
nm i figured it out.

---

### Post by dannyboy79 on 2006-10-25
it's always a good idea to post HOW you solved it not just post back saying you figured it out. This way another person won't start another thread asking the same thing, they'll find the solution using a search cause you would have the way you solved it listed in the thread as well. thank you.

---

### Post by dejitarob on 2006-11-14
I got the same thing for the Gaim 2.0 beta 5. Installing the libxml-parser-perl package fixed this for me. I also had to install libxml2-dev as well.

---

