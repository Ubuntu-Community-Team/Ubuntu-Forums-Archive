---
title: "Installing StarOffice 7 for Linux"
date: 2005-07-05
forum: General Help
---

### Post by learn25 on 2005-07-05
Hi everybody!

I have downloaded StarOffice 7 designed for linux under "educational license" at [www.sun.com](www.sun.com). 

I am using Staroffice in school but under windows since its easy to install its windows version.

Anybody can help me how to install this software (StarOffice 7 for linux) under Ubuntu linux?

I prefer to use StarOffice 7 because it has better features compared to OpenOffice.org.

Thanks in advance and more power Ubuntu!

---

### Post by ACK!! on 2005-07-05
[QUOTE=learn25]Hi everybody!

......

Anybody can help me how to install this software (StarOffice 7 for linux) under Ubuntu linux?

I prefer to use StarOffice 7 because it has better features compared to OpenOffice.org.

Thanks in advance and more power Ubuntu![/QUOTE]

Ok man, check out this page first.

[http://arc.utsc.utoronto.ca/soffice/7/doc/setup_guide/part_4.html#45](http://arc.utsc.utoronto.ca/soffice/7/doc/setup_guide/part_4.html#45)

Now for the impatient soul who does not want to click links and read instructions on other pages.

sudo ./so-7-ga-bin-{platform}-{lang}.bin -net

instead of loggin as root in Ubuntu you use sudo and give your user password to perform the root action.

Just go and follow the prompts in the gui install remembering to add this package to the /opt/<app-name> directory.  Why?  In unix tradition opt is reserved for 3rd party commercial apps <app-name> = whatever directory name StarOffice prefers to use.

---

