---
title: "Saving websites..."
date: 2005-06-30
forum: General Help
---

### Post by YourSurrogateGod on 2005-06-30
Is there any way that I could download an entire website so that I could look at it later on with Friefox or some other Ubuntu tool?

---

### Post by musicman2059 on 2005-06-30
In FireFox: File -> Save Page As...

---

### Post by YourSurrogateGod on 2005-06-30
[QUOTE=musicman2059]In FireFox: File -> Save Page As...[/QUOTE]
No, not just a webpage, but a whole website. For example, I would like to download [this](http://maven.smith.edu/~thiebaut/ArtOfAssembly/artofasm.html) site onto my hard-drive and be able to access it offline. The above method is extremely tedious.

---

### Post by musicman2059 on 2005-06-30
Ah, my bad.  In that case there's no trick that I know of.

---

### Post by SYD2005 on 2005-06-30
[QUOTE=YourSurrogateGod]Is there any way that I could download an entire website so that I could look at it later on with Friefox or some other Ubuntu tool?[/QUOTE]
Hi,

You could use the Scrapbook extension in Firefox. This allows you to download the entire site. While all the pages arnt linked together as suck it may serve what you need. Also you could use Spiderzilla which goes further and recreates the whole structure of the site and recreates all the links as well. Please remember that this practice though, is frowned upon in some cases...

Here are the links: 

Scrapbook: [http://amb.vis.ne.jp/mozilla/scrapbook/](http://amb.vis.ne.jp/mozilla/scrapbook/)
Spiderzilla: [http://spiderzilla.mozdev.org/](http://spiderzilla.mozdev.org/)

Cheers

---

### Post by virgule on 2005-06-30
I recall **iCab**<www.icab.de> could do that I have yet to find a similiar utility for Linux. I have not searched a lot tho.. Im used to believe wget would let me download more than just a single file as in:
```

wget www.website.fun/travel_pics/summer04/*.jpg

```
...to download all .jpg files.

---

### Post by bdamon on 2005-06-30
[QUOTE=YourSurrogateGod]No, not just a webpage, but a whole website. For example, I would like to download [this](http://maven.smith.edu/~thiebaut/ArtOfAssembly/artofasm.html) site onto my hard-drive and be able to access it offline. The above method is extremely tedious.[/QUOTE]


wget will pull entire web sites with ease. I believe you will need to use -r for recursive. 

Docs and some examples- [http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)


Ben

---

