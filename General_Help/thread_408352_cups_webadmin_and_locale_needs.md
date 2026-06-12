---
title: "cups webadmin and locale needs"
date: 2007-04-13
forum: General Help
---

### Post by dmizer on 2007-04-13
i have a dapper headless (command line only) file server set up for our small office and it's performing fantastically.  in addition to being a file server, it also provides for ftp access from other offices, and has a lamp intranet site set up for common webapps like scheduling, contact lists and such.

i have also been able to set up the server to host the network printers.  and here's where my problem comes in.  within a month, i'm starting a new job at a separate company, and i need to leave someone with the ability to administrate the machine, but they are japanese and speak/read very little english.

is there some way i can enable japanese support for the cups webadministration? iow ... [http://localhost:631](http://localhost:631) i dug around at the cups.org website, but couldn't find anything.  but i find it difficult to believe that a protocol that's been around as long as cups doesn't have locale transportability.

---

### Post by iXneonXi on 2007-04-13
This is a wild guess, but try checking the "cupsd.conf" for an option involving localization such as charsets and language. Change it to the code for japanese (jp?).
Back up the conf file before you do this, because I have no idea if it will work. Best bet would be to do that and restart CUPS.

---

### Post by dmizer on 2007-05-22
well ... by sheer accident i discovered that i don't have to change a thing.  the cups interface displays encoding according to browser preference.  so japanese computers view the cups interface in japanese, and english computers view the cups interface in english.

---

