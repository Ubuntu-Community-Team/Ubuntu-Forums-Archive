---
title: "wget command"
date: 2013-02-20
forum: General Help
---

### Post by gennatolls on 2013-02-20
```
wget --user=gennatolls --password='MySuperSecretPassword' http://www.website.com/file/2013/02feb.pdf
```I got tired of manually going to a website, logging in and downloading the pdf magazine. 
I just run this command from terminal to easily get my magazine. This is a monthly magazine so they update the link every month. So for marches issue it would be:

[http://www.website.com/file/2013/03march.pdf]("http://www.website.com/file/2013/03feb.pdf").

I wish you could use the wildcard "*" but it gives back a nasty message saying wildcards are not supported with http.

Any ideas?

Regards

---

### Post by Impavidus on 2013-02-20
Add a few lines to your script using **date** to get the right path/file name. If you wish you can even add the script to cron to have it run automatically once every month.

---

### Post by tgalati4 on 2013-02-20
Sometimes the website will have an RSS feed and that is easier to parse to find new issues.  Also you can use curl (*man curl*) to get more flexibility for parsing syntax.

Look at the page source for Full Circle's magazine feed:

[http://fullcirclemagazine.org/feed/](http://fullcirclemagazine.org/feed/)

To get some ideas on how to parse for new issues for your script.

If you gave us the real magazine link, then we could be more helpful.

---

### Post by prodigy_ on 2013-02-20
If they always use short month name, one-liner is enough:

```
wget --user=gennatolls --password='MySuperSecretPassword' http://www.website.com/file/$(date +%Y/%m%b).pdf
```

But it seems they don't (03march), so you'll need two lines. Example:

```
#!/bin/bash
month_names=( element_zero 01jan 02feb 03march 04april 05may 06june 07july 08aug 09sep 10oct 11nov 12dec )
wget --user=gennatolls --password='MySuperSecretPassword' "http://www.website.com/file/$(date +%Y)/${month_names[$(date +%m)]}.pdf"
```

---

### Post by gennatolls on 2013-02-20
Thanks for all the ideas. I think once i get it working I will run it automatically using cron.

Heres one I tried, its just hard to verify it work correctly every month since ill have to wait a year to confirm it.

```
wget --user=gennatolls --password='MySuperSecretPassword' http://www.website.com/file/2013/{01jan,02feb,03mar,04apr,05may,06june,07july,08aug,09sept,10oct,11nov,12dec}.pdf
```

This is all assuming they use the same month abbreviations I have used.

---

### Post by Vaphell on 2013-02-20
can't you check what abbreviations they use? There is no archive? You could even figure it out by trial and error. And you really should use date command so you know what year it is

```
$ date +%Y
2013
$ echo http://www.website.com/file/$( date +%Y )/stuff.pdf
http://www.website.com/file/2013/stuff.pdf
```

---

### Post by gennatolls on 2013-02-21
Ill throw that date command in as well. As far as I know they dont have an archive.
Many thanks for all the advice.

---

