---
title: "changing webserver default 404 page"
date: 2007-08-04
forum: General Help
---

### Post by phillips321 on 2007-08-04
Hi guys,

I would like to change the default 404 Page not found page.

I use thttpd but cannot find any referencing to this.

If you browse to my page [www.phillips321.co.uk/pictures.html](www.phillips321.co.uk/pictures.html) then click on gemma then on a thumbnail that is not there you will notice the ugly 404 screen, how do i change this?

cheers

---

### Post by merlinus on 2007-08-05
Create a page

.htaccess

and place only this text in it:

ErrorDocument 404 [http://www.phillips321.co.uk/error.html]("http://www.phillips321.co.uk/pictures.html/error.html")

Then create error.html as a regular webpage with any content you like.

-merlin

---

### Post by phillips321 on 2007-08-05
magic, cheers mate

works a treat now

---

