---
title: "&quot;Can't locate XML/Parser.pm&quot;"
date: 2006-07-07
forum: General Help
---

### Post by zrothe on 2006-07-07
I am trying to install the teatimer applet.

./configure bombs with error:

> checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

So then I did: /usr/bin/perl -e "require XML::Parser" and it gave me:

> 
Can't locate XML/Parser.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at -e line 1.

I have searched around, but I found nothing. Any help would be appreciated. Thanks.

---

### Post by zrothe on 2006-07-07
> **zrothe said:**
> I am trying to install the teatimer applet.

./configure bombs with error:



So then I did: /usr/bin/perl -e "require XML::Parser" and it gave me:



I have searched around, but I found nothing. Any help would be appreciated. Thanks.

We'll it turns out it's in the rep. as teatime (I tried teatimer). So I have it now, but I would still like to figure out this XML prob for future use and I have run into this once before.

---

### Post by Appolusionist on 2006-07-07
> **zrothe said:**
> We'll it turns out it's in the rep. as teatime (I tried teatimer). So I have it now, but I would still like to figure out this XML prob for future use and I have run into this once before.

You can install XML Parser by install the libxml-dom-perl. I can't remember off the top of my head if you have to add any repositories.

```
sudo apt-get install libxml-dom-perl
```

---

