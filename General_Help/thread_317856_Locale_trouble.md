---
title: "Locale trouble"
date: 2006-12-13
forum: General Help
---

### Post by juraj on 2006-12-13
I'm using edgy eft.

I changed my system's locale setting with dpkg-reconfigure localeconf. And it's all right. GDM on login shows my language's date format properly. Yippee.

However, on my main account, ALL locales are still the ones they were before! And date format is wrong! Where to change this? I've even tried creating a new account. It displays everything how it should, all locales are correctly set up there.

Ubuntu SERIOUSLY lacks locale configuration tools - what if I want it to use my language's date format, and retain english menus? I have to use the command line! (not that it's hard, but what about inexperienced users? In Windows, all of this is very easily configured in Regional settings... everything, date format, monetary format....).

And now that I've configured it properly, my account still uses old settings :(

Please help.

---

### Post by tenjin on 2006-12-13
Hi,

I'm saying this will fix your issues, but I had some date-related problems with Edgy.

I had to set the locale in:

/etc/environment

- and

/etc/default/locale

- adding the following line:

LANG="en_GB.UTF-8"

That seemed to do the trick for me.

Cheers

D.

---

### Post by sizzlor on 2007-01-27
hmmm... i was trying to apply the above to get rid of the silly American date / time formats used by **Evolution**, but it's no good. 
Evolution just does its own thing, and i'm left to guess WTF **"08/05/07"** is supposed to mean.. ugh.

---

