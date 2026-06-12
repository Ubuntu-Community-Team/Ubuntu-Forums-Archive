---
title: "migrate itunes collection with rating and playlists"
date: 2008-03-26
forum: General Help
---

### Post by komputes on 2008-03-26
Getting ready to go all Linux, one of two things I need is to import my itunes collection. Is there a way to import an iTunes Music collection to a linux program (amarok/rythmbox), keeping ratings and playlists intact?

---

### Post by scramasax on 2008-03-26
> **komputes said:**
> Getting ready to go all Linux, one of two things I need is to import my itunes collection. Is there a way to import an iTunes Music collection to a linux program (amarok/rythmbox), keeping ratings and playlists intact?

Not sure how either Amarok or Rhythmbox stores such data, and my iTunes and Rhythmbox libraries are totally separate and use different formats (mp4 (i.e. AAC) and ogg vorbis), anyway, so I've never tried going between the two.  But if if either Amarok or Rhythmbox stores such data as XML then I'd think it possible, because iTunes can export to XML.  So what you'd need to do is to use XSLT to transform the output from the one application to that the other application expects.  I suspect that would be more labour than it's worth, however.

---

### Post by strabes on 2008-03-26
From a simple [search](http://ubuntuforums.org/search.php?searchid=38411989) on ubuntuforums.org I was able to find the following information from various threads:

[https://launchpad.net/itunes-export](https://launchpad.net/itunes-export)
[http://zanfishen.com/delights/itunesratings.html](http://zanfishen.com/delights/itunesratings.html)

Your success may be limited as iTunes' library is proprietary and thus not easily imported with other players. You will most likely need to retag some of your files because iTunes' tagging system is also awful. For this task I recommend easytag:```
sudo aptitude install easytag
```

---

