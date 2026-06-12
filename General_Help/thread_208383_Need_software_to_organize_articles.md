---
title: "Need software to organize articles"
date: 2006-07-03
forum: General Help
---

### Post by silent82 on 2006-07-03
Hello,
I'm a content responsable of 2 magazines. I'm searching a software to manage articles. I need a database for authors, articles, images and manazines. I need a software that let's me store articles, assign images to each article, and sign where (on which magazine) and when each article is publicated...

Is such software available for GNU/Linux?
Any kind of help is wellcome!

Thanks!

---

### Post by nanotube on 2006-07-03
looks like you are looking for a bibliographic manager software. one i use to keep track of finance/econ articles is called jabref (jabref.sf.net). there's also pybliographer, wikindx (runs through a web server though, so not that simple to set up), and many others. jabref itself is not available in the repositories, but there are probably a few that are. just search in synaptic for "bibliography" or "bibliographic" (make sure to enable the universe and multiverse repositories first), and you will get some results.

---

### Post by silent82 on 2006-07-04
Great!

I don't need to set it up on a webserver, so I discarded wikindx. The choice is between jabref and pybliographer. jabref seems more complete than pybliographer and it's in java... I can let the editor download it and send him the article database each month. I had to customize the fields and create another type of article, because I also need to store the text of the articles in the database. I think JabRef saved me a lot of money and time...

Tanks nanotube!

---

### Post by jethro10 on 2006-07-04
Would using the beagle search not be enough?,

It can search inside files and inside images for the tags, etc.

It would pull up all entities that matches a keyword or combination thereof.

J

---

### Post by nanotube on 2006-07-04
[QUOTE=silent82]Great!

I don't need to set it up on a webserver, so I discarded wikindx. The choice is between jabref and pybliographer. jabref seems more complete than pybliographer and it's in java... I can let the editor download it and send him the article database each month. I had to customize the fields and create another type of article, because I also need to store the text of the articles in the database. I think JabRef saved me a lot of money and time...

Tanks nanotube![/QUOTE]
glad i could help :)

---

### Post by hvbakel on 2006-07-04
you might also want to try 'bibus' (just do a search on google). It also manages references and provides very good integration with openoffice for citations etc.

---

### Post by silent82 on 2006-07-05
Actually none of the softwares mentioned really works for me. I need to organize articles (even text and photos), I need a database for each media where articles could be published and I should be able to sign where each artile has been published and when. All the software I tried does more complex things, but it doesn't do what I need... I'm starting to consider the development of my own software...

---

### Post by jayemef on 2006-07-05
I have two suggestions to add: GLibrary and TreeLine. The former is a relatively simple book collection manager based on GTK. Honestly, it sounds like it doesn't have the features you're looking for, but it might prove useful to others so I've listed it. The second, and hopefully more promising for you, is really cool because it allows you to store any sort of data as a tree, providing a middle ground between a database and personal information organiser. The nice thing too is its export ability, which will allow you to export it to XML, CSV, plain text, etc. As I've said, it can be used to organize pretty much anything, so it might be of use to you.

---

### Post by hugmenot on 2006-07-06
You could try glom for a simple DIY database. The development effort would be limited

---

### Post by silent82 on 2006-07-06
glom is the most flexible software I've seen so far, the problem is that is uses only postresql, I would like to use sqlite... Kexi seems interesting... I just found also Gemello ([http://www.fuhringer.com/gemello/](http://www.fuhringer.com/gemello/)) bus seems very poor...

Is thare something like kexi for gnome that uses sqlite?

---

### Post by hugmenot on 2006-07-06
Why do you insist on Sqlite?

---

### Post by silent82 on 2006-07-06
because I could easly backup an sqlite database, and I could simply create a php search form... It's a practical thing...

---

