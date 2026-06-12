---
title: "Squid Configuration"
date: 2006-11-19
forum: General Help
---

### Post by christodoulos77 on 2006-11-19
I have squid and its ranning very nice.
But I noticed that when I'm downloading an .exe file from widows,
and I try to download the same file again from the same URL,
it's download the file from the URL insted from the cache.

Can anyone help?

---

### Post by christodoulos77 on 2006-11-19
Please.. help ! ! !

---

### Post by christodoulos77 on 2006-11-20
Heeeeeeeelp!!!!!!!!!!!!!!!!!!!!!

---

### Post by Faheem on 2006-11-21
Hi

i am a newbie to squid so I could be wrong but squid caches http requests or the pages so I dont think it would cache an exe file. I could be mistaken. Maybe someone else will be of more help.

---

### Post by christodoulos77 on 2006-11-22
When i'm downloading an .exe or .zip file what kind of request is this?

---

### Post by esaym on 2006-12-04
Squid can cache any file.  I do not have the info off hand right now but you can force squid to never check the freshness of exe files.  Also another problem might be that the exe file is bigger then the max file size limit.


Ok i just found what i was talking about.  

refresh patterns:


refresh_pattern -i .exe$ 129600 100% 129600

The -i means not case sensitive and i for got what the $ mean and what the numbers mean.  Do a search and look them up.  Also the smoothwall forums might be a good place to go for info since smoothwall comes with squid.  I got alot of stuff posted on there too...

---

