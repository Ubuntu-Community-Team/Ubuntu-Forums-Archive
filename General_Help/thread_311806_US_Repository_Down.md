---
title: "US Repository Down"
date: 2006-12-03
forum: General Help
---

### Post by maddog39 on 2006-12-03
Hello all,

I have been trying to access the repository today and the US mirror seems to be down. I cant download anything from us.archive.ubuntu.com, before I was installing Deluge and it took 3-4 minutes to recieve a reply and ping requests were taking 40secs-1minute to recieve. Now it's not responding at all. Sounds like a DDoS to me. But wouldn't really no. Anyone else experiencing problems with the US repos today?

-maddog39

---

### Post by taurus on 2006-12-03
Remove the us from those repos in /etc/apt/sources.list!

---

### Post by loyd86 on 2006-12-03
I have the same problem ](*,)

How do I fix it to look at a differnt mirror?

---

### Post by FeraTech on 2006-12-03
Yes, I tried all day today as well and the repositories seem to be down. Earlier today though they were working intermittently.

---

### Post by atoponce on 2006-12-03
loyd86- edit your /etc/apt/sources.list, and search/replace the current url with an official mirror listed at download.ubuntu.com.

---

### Post by FeraTech on 2006-12-03
Removing the us. works.

Thanks, I had that done before actually because the us. repos were down.

---

### Post by maddog39 on 2006-12-04
Okay well I did what you told me and it messed it up even more, now every time I try to install a package I get, a type of "not compatible with your system hardware" error.

---

### Post by taurus on 2006-12-04
> **maddog39 said:**
> Okay well I did what you told me and it messed it up even more, now every time I try to install a package I get, a type of "not compatible with your system hardware" error.
Well, let's have a look at your /etc/apt/sources.list then!

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by maddog39 on 2006-12-04
Hmm well I got it to revert back to the default via:
```

sudo mv /etc/apt/sources.list.save /etc/apt/sources.list

```
so now it works fine.

---

