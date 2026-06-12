---
title: "Apt-Get Question - Search Repositories?"
date: 2006-10-30
forum: General Help
---

### Post by BarfBag on 2006-10-30
Hello,

I have a simple question about apt-get.  Is there a search command that will search the repositories and find results similar to the word I put in?  When I do sudo apt-get install whatever, it looks for the exact word and nothing similar.

Thanks,
BarfBag

---

### Post by ~LoKe on 2006-10-30
```
sudo apt-cache search xxx
```

---

### Post by Bukunut on 2006-10-30
BarfBag

If I understand your question correctly are you referring to the search facility in apt-get ...

> apt-cache search WORDTOSEARCH

Bukunut

---

### Post by aysiu on 2006-10-30
You can also do ```
aptitude search *what you're looking for*
``` [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

