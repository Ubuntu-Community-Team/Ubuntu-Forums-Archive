---
title: "PHP 5.4 and old Ubuntu"
date: 2023-06-11
forum: General Help
---

### Post by Drenriza on 2023-06-11
Hi All
I need to install a server with PHP 5.4, and was hoping for some input on this.

What would be the newest Ubuntu LTS version available, where PHP 5.4 would be possible to install?

I am also unfamiliar with how the repository mirrors works on versions that old, are packages still available in official repos
or how does that work?

Thank you all in advance
Best regards

---

### Post by Holger_Gehrke on 2023-06-12
According to php.net, 5.4.0 was released in March 2012 and 5.4.45 was released in September 2015. Precise (12.04) came with PHP 5.3 and Trusty (14.04) came with 5.5, so if 5.4 was ever officially packaged it was for one of the short time support releases in between those.

The packages for out of support old releases aren't in the official repositories, they are moved to 'old-releases.ubuntu.com'.

If it was me, I'd try to get the source for that version of php and try to compile it on a current release of Ubuntu, less risky than running an old release of the OS.

Holger

---

### Post by SeijiSensei on 2023-06-13
I suggest you compile it from source using git. 

[https://www.php.net/git.php](https://www.php.net/git.php)

I browsed the git repository. You probably want start here. 

[https://github.com/php/php-src/tree/PHP-5.6.40](https://github.com/php/php-src/tree/PHP-5.6.40)

It's the most recent release of version 5. 

If you've never compiled anything from source code before, this will take a bit of time, but there's good documentation of the steps involved.

Before doing this you'll need to install the build-essential package which includes the GNU C++ compiler and associated files.

```
sudo apt install build-essential
```

---

### Post by Drenriza on 2023-06-14
Hi All
Thank you for your insight and suggestions, this is a great starting point!

Best regards

---

