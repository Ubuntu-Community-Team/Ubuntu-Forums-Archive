---
title: "Rhythmbox XML database query"
date: 2008-06-10
forum: General Help
---

### Post by gausie on 2008-06-10
Hey everybody

I've got a list of songs that I want to mark with a rating of 5 in my rhythmbox database, and its a huge list so i can't do it manually.

Were this in sql, i would run a query using each line of my list finding the record with that filename, and editing the rating field, but since this is XML, I don't really know how to do that.

Any suggestions from anyone?

Gausie

---

### Post by HalPomeranz on 2008-06-10
There's some Python code at:

[http://hicks-wright.net/blog/itunes-and-rhythmbox-ratings/](http://hicks-wright.net/blog/itunes-and-rhythmbox-ratings/)

It will give you an example of parsing the Rhythmbox XML database and updating the ratings values.  It's almost certainly more complicated than what you're looking for, but you can just chop out the parts you need.

---

