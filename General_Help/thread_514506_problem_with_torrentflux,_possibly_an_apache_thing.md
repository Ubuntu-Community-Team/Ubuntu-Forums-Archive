---
title: "problem with torrentflux, possibly an apache thing"
date: 2007-07-31
forum: General Help
---

### Post by yellowband on 2007-07-31
hi

i posted this over at the torrentflux forums but they aren't active and i doubt i'll find the help im looking for.  Basically i installed torrentflux via apt-get, but the files weren't installed in my webroot directory /var/www.  What happened and what can i do to fix this problem?  here is what i posted before:

I have installed torrentflux onto my ubuntu 7.04 desktop.  when i go to localhost/torrentflux, i get an error saying something along the lines of "access database error for  user....) it then tells me to check my config file.  I think i can figure the database stuff out, but what is stumping me is that, it doesn't appear that torrentflux was installed in my apache web root directory /var/www/. 

I find it strange that a page shows up at all when i go to localhost/torrentflux in my browser, yet there are no torrentflux files in my /var/www/ directory. 

How can i access my torrentflux config file if its not in the web directory (php needs to be parsed by the webserver) and furthurmore, how is torrentflux working at all (communicating with my browser) when there are no torrentflux files in the webserver webroot directory?

thanks alot for any help.

---

### Post by yellowband on 2007-08-01
any ideas on this?

or maybe a tutorial on how apache's web root works?  i'm totally baffled as to how i have a localhost/torrentflux page yet no torrentflux files are in my webroot folder....

---

