---
title: "PHP Pear Issue"
date: 2016-02-24
forum: General Help
---

### Post by SchnappiJedi on 2016-02-24
Hi,

Ever since ran "sudo pear channel-update pear.php.net"  "sudo apt-get --purge remove pear" doesn't work and returns the following:
[I]
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package pear
[/I]
"sudo apt-get install pear" also returns the below so believe it is an issue with the channel-update command:[I]
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package pear
[/I]
What is the original pear channel ("sudo pear channel-update CHANNEL")?

---

### Post by SeijiSensei on 2016-02-25
On my 14.04 machine, it appears the package is called "php-pear" not simply "pear".

Packages often have names different from what you might expect.  One simple check is to run something like
```
apt-cache search pear | grep pear
```
which returns a list of packages with "pear" in them.  Along with "php-pear" I see "pear-channels".

---

### Post by SchnappiJedi on 2016-02-28
You were right. Feel dumb. The package is called "php-pear"

---

### Post by SeijiSensei on 2016-02-29
Given that some PHP packages start with php- and others start with php5-, I see no reason for you to feel sheepish.  Package naming conventions are just not that consistent.  Apt-cache search can help a lot, though.

---

