---
title: "Terminal automatically copy all text from website into text file. Possible?"
date: 2013-05-24
forum: General Help
---

### Post by BudworthTDog on 2013-05-24
Does anyone know if this is possible? Can I give the terminal a web address and pipe the text from that page to a text file?

I was pretty sure it wasn't going to work but I figured what the heck I will give it a go before I post something. I tried

firefox [www.examplesite.com](www.examplesite.com) >> textfile

If it is possible I would like the code to addon to the end of an existing text file and not overwrite in completely. From my understanding thats what >> will do

---

### Post by diesch on 2013-05-24
```
wget http://www.example.com -O- >> textfile
```

---

