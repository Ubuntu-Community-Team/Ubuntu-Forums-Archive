---
title: "Unrar multiple archives"
date: 2008-04-22
forum: General Help
---

### Post by bioShark on 2008-04-22
Hi

I am using Kubuntu 7.10. I want to unrar an archive which contains more smaller archives, like r01..r21. I have installed unrar-free, but when I run:

```
 unrar-free -x <archive>.rar
```

I get the following:

```
Extracting from <path><archive>.rar

Extracting  <archive>.avi                     Failed
1 Failed
```

I have tried this alo with the .rar, .r00 and .r21 (the last archive). It's the same result. 

On windows it works, so the archive is not corrupt.


Thanks.

P.S. Does it matter that the archive contains several "." characters?

---

### Post by gsmanners on 2008-04-22
The free version can't handle multi-volume. For that, you need the non-free version (unrar or rar).

---

### Post by bioShark on 2008-04-22
But it's Linux...it's suppose to be free :)))).
Where can I find a free package?

---

### Post by mali2297 on 2008-04-22
> **rollandsov said:**
> 
P.S. Does it matter that the archive contains several "." characters?

No.

> **rollandsov said:**
> But it's Linux...it's suppose to be free :)))).
Where can I find a free package?

You can install **unrar-nonfree** from Synaptic. Check that the *multiverse* repository is enabled (via Settings -> Repositories). Then use the search function in Synaptic to find the package.

The *nonfree* part means here that it is not open-source. It is still free as in beer.

EDIT: I just realized that you might not have Synaptic in Kubuntu, use Adept instead.

---

### Post by bioShark on 2008-04-22
Hi

Thanks, I'll try that.

Don't worry about Synaptic and Adept. I know both of them. I've used Ubuntu too, but I just like KDE.

---

### Post by bioShark on 2008-04-23
Hi

It worked, thanks a lot. So unrar-nonfree was the solution.

c.u.

---

