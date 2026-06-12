---
title: "Vi highlighting help needed"
date: 2008-02-19
forum: General Help
---

### Post by gryfen on 2008-02-19
Hi,

While editing a script in vi, I accidentally fat fingered some keys, and now every 'r' in the script is highlighted.  When I exit vi, all is normal, but when I go back into any file using vi, all the 'r's are highlighted again.  I can't figure out how to turn this off.

Please help :)

Thanks,

G

---

### Post by HermanAB on 2008-02-19
I think that vi highlighting is spelled 'gedit'...

---

### Post by orlox on 2008-02-19
what you probably did was a search. The command:

```

/r

```

should make vi look for all "r" in the file and highlight them (:/r is equivalent). I dont remember quite well a nice way to take the highligting away, but you can do this by using an absurd search of something that cant be found, like:

```

/$%)

```

or anything similar...If anyone knows the decent way, please tell, that i've also been anoyed by this thing sometimes.,..

---

### Post by orlox on 2008-02-19
apparently, the decent fix is to run the command:
```

:nohlsearch

```
It's a bit long thouhg, takes less time to do a stupid search :P

---

