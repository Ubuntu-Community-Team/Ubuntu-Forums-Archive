---
title: "24 hour time? ... We're in the army now!"
date: 2006-08-17
forum: General Help
---

### Post by peabody on 2006-08-17
My Gnome clock applet seems to be stuck on 24 hour time.  When I right click and select properties, there isn't an option to switch to 12-hour time.  Even trying to manually set the right value via gconf-editor doesn't switch the clock applet to 12-hour time.  Anybody else experience this before or am I just special?

---

### Post by IYY on 2006-08-17
For me it's right click > preferences > clock type > 12 hour, on Dapper.

---

### Post by peabody on 2006-08-17
> **IYY said:**
> For me it's right click > preferences > clock type > 12 hour, on Dapper.

Yes I believe it was that way for me too until recently.  I can't imagine why it's stopped working.

---

### Post by aysiu on 2006-08-17
Are you saying that when you right-click the clock, you don't get *preferences*?

---

### Post by peabody on 2006-08-17
No I do, the menu in the dialog I've attached is the problem.  It only lists three things, 24 hour, Unix time and Internet Time.  I even found the gconf entry this dialog sets and setting it manually to 12-hour didn't do anything either.

---

### Post by theratster on 2006-08-17
Yeah, just click the "24 hour" (its a pulldown menu) and set it to 12...

---

### Post by aysiu on 2006-08-17
Yes, just click on *24 hour*, and you'll get other options.

If the change isn't taking, you might want to do ```
sudo chown -R peabody:peabody /home/peabody
```

---

### Post by peabody on 2006-08-17
> **theratster said:**
> Yeah, just click the "24 hour" (its a pulldown menu) and set it to 12...

12-hour is not in the drop down list for me.

I have my suspicions that one these repositories are the culprit:

# Xgl, compiz stuff
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

# Cipherfunk
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

Lot's of screwy things have been going on lately to my machine like stuff that my gnome-terminal depends on being updated from [www.beerorkid.com](www.beerorkid.com) and my freetype library being updated to something that has the bytecode interpreter turned off :-x (ugly truetype fonts!  Blech!).  Anybody else using these repositories experiecing weirdness?

---

### Post by yopnono on 2006-08-17
> **peabody said:**
> 12-hour is not in the drop down list for me.

I have my suspicions that one these repositories are the culprit:

# Xgl, compiz stuff
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

# Cipherfunk
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

Lot's of screwy things have been going on lately to my machine like stuff that my gnome-terminal depends on being updated from [www.beerorkid.com](www.beerorkid.com) and my freetype library being updated to something that has the bytecode interpreter turned off :-x (ugly truetype fonts!  Blech!).  Anybody else using these repositories experiecing weirdness?

The clock format depends on which language you are using like en_dk =24h clock, en_us=AM,PM. So check your language setting. under language support

---

### Post by peabody on 2006-08-17
> **yopnono said:**
> The clock format depends on which language you are using like en_dk =24h clock, en_us=AM,PM. So check your language setting. under language support

yopnono you rock!  That was it.  For some reason, my language settings
got set to English (Zimbabwe).  W-E-I-R-D.  Problem solved.

---

