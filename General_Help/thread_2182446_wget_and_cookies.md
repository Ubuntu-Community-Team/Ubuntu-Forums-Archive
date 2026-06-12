---
title: "wget and cookies"
date: 2013-10-21
forum: General Help
---

### Post by davidtuti2 on 2013-10-21
Hi!
  I'm trying to authenticate with wget in a forum but I cant.
  I do:
```
   wget --save-cookies cookies.txt --post-data 'username=USER&password=PASS' http://www.yoloestoyviendo.com/index.php
   wget --load-cookies=cookies.txt http://www.yoloestoyviendo.com/index.php --timeout=60 -O OUTPUTFILE.TXT

```   
But when I see the output file I check that I not logged in.
Please any help? Many thanks and sorry for my english!

---

### Post by apmcd47 on 2013-10-21
> **davidtuti2 said:**
> Hi!
  I'm trying to authenticate with wget in a forum but I cant.
  I do:
```
   wget --save-cookies cookies.txt --post-data 'username=USER&password=PASS' http://www.yoloestoyviendo.com/index.php
   wget --load-cookies=cookies.txt http://www.yoloestoyviendo.com/index.php --timeout=60 -O OUTPUTFILE.TXT

```   
But when I see the output file I check that I not logged in.
Please any help? Many thanks and sorry for my english!

I had to write a similar script recently. Try this:
```
   wget --save-cookies cookies.txt --post-data 'username=USER&password=PASS' [COLOR="#FF0000"]--cookies=on --keep-session-cookies[/COLOR] http://www.yoloestoyviendo.com/index.php
   wget [COLOR="#FF0000"]--keep-session-cookies[/COLOR] --load-cookies=cookies.txt http://www.yoloestoyviendo.com/index.php --timeout=60 -O OUTPUTFILE.TXT

```

Andrew

---

### Post by davidtuti2 on 2013-10-21
Thanks Andrew but it seems that doesn't works :(

---

