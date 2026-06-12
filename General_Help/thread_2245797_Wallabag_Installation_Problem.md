---
title: "Wallabag Installation Problem"
date: 2014-09-26
forum: General Help
---

### Post by macstar on 2014-09-26
i have big problems to install the latest wallabag on my system. www directory on my apache server is writable, but whenever i want to install wallabag i get the error:
*"Installation aborted, impossible to create inc/poche/config.inc.php file. Maybe you don't have write access to create it."*

when i manually copy/rename config.inc.default.php to config.inc.php, the message remains!

i found not a single (!) unfaulty installation guide to this and thought it would be rather easy, as i successfully run bandwidthd and loganalyzer without any problem so why is this not working? :mad:

---

### Post by wayne17 on 2015-01-31
I found that running this command in the install directory solved the problem: sudo chown -hR www-data inc 
You also want to run the same command changing only the inc part for assets, db and cache if you haven't already given the web server user permissions to those directories. It took me many many hours to try to figure this out so I really want to get this out there cause no one tells you most of this stuff.
 You also want to make sure port 9000 is not blocked by your firewall on the server or else it will mess up the installation.(This only applies to nignx.) And in the event that it gets stuck on the install page run this in the install directory (be careful to copy all of it as it can be dangerous if you don't) : sudo rm -r cache/* install/
and I may make my own guide on this as none of the guides address these possible problems and the first one happens 100% of the time without anyone telling you how to fix.

---

