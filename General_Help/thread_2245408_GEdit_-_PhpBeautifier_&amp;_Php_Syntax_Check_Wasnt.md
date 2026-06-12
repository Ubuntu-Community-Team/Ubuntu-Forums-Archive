---
title: "GEdit - PhpBeautifier &amp; Php Syntax Check Wasnt Working"
date: 2014-09-23
forum: General Help
---

### Post by tagra123 on 2014-09-23
After upgrading  (clean install) to 14.04

I couldnt get PHP Beautifier, or php -l to work on the command line or inside of gedit.

To make it work I changed

display_errors = on   (This was around line 479)

in the file /etc/php5/cli/php.ini

Works now.

---

