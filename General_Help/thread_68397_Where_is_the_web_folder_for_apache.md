---
title: "Where is the web folder for apache?"
date: 2005-09-23
forum: General Help
---

### Post by Zensunni on 2005-09-23
Okay, I'm completely new at this and have been getting around OK on ubuntu. I've installed apache2 and it works fine on the network.

But, I don't know where to put all my web site documents that I want to load into the server. I tried "/var/www", but that only shows all my web-files on a list, instead of just sending the browser to the index.html file.

When I use the windows version, I just plop my content into the "htdocs" folder and away I go. I was thinking that there might be a command to make the "www" folder behave like the htdocs folder in windows.

Or, maybe the htdocs folder is on the ubuntu installation and I just can't find it.

Any help?

BTW, I'm very impressed with this new linux. It has a tonn of cool features.

---

### Post by vayu on 2005-09-23
/var/www is the place on my system.  Maybe your apache settings have directory browsing on.  And maybe they don't have index.html set as the default document type.  Regardless, you should be able to access your page by going to a browser and typing either [http://localhost/index.html](http://localhost/index.html) or [http://127.0.0.0/index.html](http://127.0.0.0/index.html).

---

### Post by Zensunni on 2005-09-23
*scratch head*

How do you turn directory browsing off? Sorry if that's a really dumb question. I know I aught to be reading a book on this.....

---

### Post by phex on 2005-09-23
if you have not changed the default configuration of apache2 then each user of your linux operating system has his own directory where he can put his html files in. then the apache2 server can show them in the browser.
this directory is named public_html and if your user account is phex then you have a directory /home/phex. there you should create the public_html directory so that you have a path like this /home/phex/public_html. there you can put in a file myhtml.html  which can be accessed in the browser by typing [http://127.0.0.1:8080/~phex/myhtml.html](http://127.0.0.1:8080/~phex/myhtml.html).

hope that has helped you.

---

