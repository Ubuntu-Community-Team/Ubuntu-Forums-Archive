---
title: "new computer trouble"
date: 2006-10-20
forum: General Help
---

### Post by bearcat on 2006-10-20
So I bought a spiffing new computer this week...but I'm having some minor troubles getting Dapper up and running. Namely, in order to connect to the Internet, there are some files from my ISP that I need to place in /usr/local/bin - but when I try to do that, I'm told that I don't have permission to write to that folder. (I *didn't* have this problem installing Breezy on my old box, I should point out; I was able to put the files into that folder with no difficulty at all.)

So I guess what I need to know is, is there some skrewy sudo/chmod thing I have to do to the directory so that I can write to it? I'm a relative Linux newbie (not completely inexperienced, but also not familiar enough with it to figure this stuff out by myself), so I'd appreciate it if someone could help me...

---

### Post by taurus on 2006-10-20
```

sudo cp filename /usr/local/bin

```

---

