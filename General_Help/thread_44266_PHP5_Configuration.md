---
title: "PHP5 Configuration"
date: 2005-06-25
forum: General Help
---

### Post by gamehack on 2005-06-25
Hi all,

I did install PHP5 from source using this guide [https://wiki.ubuntu.com/PHP5FromSource](https://wiki.ubuntu.com/PHP5FromSource) ;) Everything went fine the only thing is that I cannot find the php.ini file for it... so I cannot configure anything. Does anyone have any idea where it could be? Because I did try to find in with locate but it only finds the template ones(php.ini-dist etc) in the source dir.

Regards

---

### Post by jarrett.wold on 2005-06-27
[http://www.php.net/manual/en/install.unix.apache2.php](http://www.php.net/manual/en/install.unix.apache2.php)

" 
13. Setup your php.ini 
    
    cp php.ini-dist /usr/local/lib/php.ini
          
    You may edit your .ini file to set PHP options.  If you prefer having
    php.ini in another location, use --with-config-file-path=/some/path in
    step 10.
    
    If you instead choose php.ini-recommended, be certain to read the list
    of changes within, as they affect how PHP behaves.
"

---

