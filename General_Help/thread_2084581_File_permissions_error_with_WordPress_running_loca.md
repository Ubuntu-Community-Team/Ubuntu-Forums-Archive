---
title: "File permissions error with WordPress running locally"
date: 2012-11-15
forum: General Help
---

### Post by gavinflud on 2012-11-15
I'm after getting WordPress up and running for the first time locally on Ubuntu (been using it on Windows for over a year).

I am simply trying to include two files in my functions.php file but it's giving me the following errors:

```
Warning: include(functions/shortcodes.php): failed to open stream: Permission denied in /var/www/kinnegad/wp-content/themes/kinnegad/functions.php on line 27

Warning: include(): Failed opening 'functions/shortcodes.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/kinnegad/wp-content/themes/kinnegad/functions.php on line 27

Warning: include(functions/theme-options.php): failed to open stream: No such file or directory in /var/www/kinnegad/wp-content/themes/kinnegad/functions.php on line 31

Warning: include(): Failed opening 'functions/theme-options.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/kinnegad/wp-content/themes/kinnegad/functions.php on line 31
```

This has worked for me in Windows but wont work on Linux and I'm assuming it's to do with file permissions. I've changed them and still no luck. Any help with this would be greatly appreciated.

---

### Post by gavinflud on 2012-11-15
Figured out the problem. It was indeed a permissions issue. Had to change the entire wp-content directory and all sub-directories to 755 and all files inside that to 644. Works perfectly now.

---

