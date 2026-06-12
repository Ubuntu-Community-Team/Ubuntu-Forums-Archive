---
title: "k9copy &amp; dual core"
date: 2007-12-27
forum: General Help
---

### Post by kefurd06 on 2007-12-27
i'm using k9copy to rip a dvd to an mpeg (xvid format). i'm noticing that it's not utilizing my dual cores. i read somewhere else that it is probably the encoding software outside of k9copy that is the problem. any idea how to fix this?

---

### Post by Termina on 2008-06-11
I came across this while googling, figured I'd post a solution. I can confirm both of my cores are being used using System Monitor when I encode.

Add:
```

-lavdopts threads=2

```

To each of the commands in preferences for the codec you're using. DivX seems to work very well with this, havn't tried anything else.

---

