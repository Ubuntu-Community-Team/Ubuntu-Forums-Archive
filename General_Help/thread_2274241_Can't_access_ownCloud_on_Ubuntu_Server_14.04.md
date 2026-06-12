---
title: "Can't access ownCloud on Ubuntu Server 14.04"
date: 2015-04-18
forum: General Help
---

### Post by joelstitch on 2015-04-18
I installed ownCloud following [**THIS **]("http://www.ubuntugeek.com/install-owncloud-on-ubuntu-14-04-trusty-tahr.html")guide but when I try to access MYWEBSITE.com/owncloud it doesn't load. Anything special I have to do to access ownCloud from outside my network?

Solution: 

Dumb me, I didnt have port 80 opened. I don't have access to my router at the moment so I opened so I changed Apache to used a different ports that I already had opened and forward it to the apache folder in /var/www/html/

---

