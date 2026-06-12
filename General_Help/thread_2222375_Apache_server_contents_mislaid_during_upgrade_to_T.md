---
title: "Apache server contents mislaid during upgrade to Trusty"
date: 2014-05-06
forum: General Help
---

### Post by halfbeing on 2014-05-06
Hello,

At some time recently, presumably during the upgrade to Ubuntu 14.04, my web server contents disappeared. I use Apache2 and my /var/www/index.html begins with the text "It works", but that is not what I see when I go to localhost in my browser. Instead I get a page that begins "Index of /". If I try to go to any page in my Dokuwiki I get a 404 error. The Dokuwiki is installed directly from the developers and independently of the Ubuntu package, in a subdirectory of /var/www . How can I get my web server, and particularly my wiki, working again?

Thanks in advance.

EDIT: I've got as far as getting apache looking in the right directory by going to /etc/apache2/sites-enabled/000-default.conf and changing Document root back from /var/www/html to /var/www, but now PHP isn't working and my wiki is displaying as a raw PHP script.

---

### Post by SeijiSensei on 2014-05-06
I suggest you reverse the process. Move what was formerly in /var/www to /var/www/html, then restart Apache with "sudo service apache2 restart" just for good measure.

---

### Post by halfbeing on 2014-05-06
Thanks for the suggestion. I tried moving everything to /var/www/html but I'm still getting the raw PHP code.

---

### Post by halfbeing on 2014-05-06
I think I have identified the problem. During my previous system upgrade Dokuwiki broke. Because of this I uninstalled the Ubuntu package in favour of a tarball direct from the developers. During the latest I upgrade I was prompted to remove a huge number of packages that had been automatically installed. I suspect that libapache2-mod-php5, a dependency of dokuwiki, was hidden among those packages. Reinstalling libapache2-mod-php5 has got everything working again.

---

### Post by SeijiSensei on 2014-05-06
That would have been my next suggestion, but I figured you already had that installed since things worked before.  I wouldn't have guessed some package would remove libapache2-mod-php5.  That breaks all PHP applications that might be running on the same machine. You did say it was an optional delete, so I guess it's not really a bug.

---

