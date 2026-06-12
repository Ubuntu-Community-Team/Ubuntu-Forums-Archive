---
title: "Grepping through logs"
date: 2008-01-23
forum: General Help
---

### Post by hoffmannick on 2008-01-23
Hello!  
This is a question for all you optimization guys (and girls) out there.
I currently and frequently have to grep through 20+ gigs of zipped logs.  This can take upwards of 9 or so hours.
The way that I do it now is 

```
zcat logs*.tar.gz | egrep -i (some expressions) | tee output
```

is there a more efficient way to do this, perhaps a faster way?  Does anyone know of any other grepping algorithms that may be a little quicker?  I'm not sure if zgrep will really save that much time on the bottom line, I understand that there is a lot of information that I'm grepping through, so I'm not looking to get it done in 5 minutes, but even just a little faster would be nice :)

Thanks!
-nick

---

