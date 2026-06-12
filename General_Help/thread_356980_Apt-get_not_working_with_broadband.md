---
title: "Apt-get not working with broadband"
date: 2007-02-09
forum: General Help
---

### Post by Rumpty on 2007-02-09
I asked about this on the networking and wireless forum, but nobody replied. Perhaps someone on this forum can help?

Using Kubuntu Dapper.

I have recently connected up to broadband, configured the ethernet card etc., after using dial-up previously. 

Initially couldn't browse the web with Firefox, but disabling IPv6 fixed that. 

Apt-get still will not work though, it can't access the repositories. After a lot of investigation on the forums, the trouble appears to be a combination of my DSL-504T router, IPv6 perhaps, and DNS lookup difficulties. I have found some possible work-arounds which are a bit messy to me, and I haven't tried them, so is there a straightforward answer to solving this please?

---

### Post by lukew on 2007-02-09
> **Rumpty said:**
> I asked about this on the networking and wireless forum, but nobody replied. Perhaps someone on this forum can help?

Using Kubuntu Dapper.

I have recently connected up to broadband, configured the ethernet card etc., after using dial-up previously. 

Initially couldn't browse the web with Firefox, but disabling IPv6 fixed that. 

Apt-get still will not work though, it can't access the repositories. After a lot of investigation on the forums, the trouble appears to be a combination of my DSL-504T router, IPv6 perhaps, and DNS lookup difficulties. I have found some possible work-arounds which are a bit messy to me, and I haven't tried them, so is there a straightforward answer to solving this please?

This was not the thread i used, there were a few more lines to add, but people have siad that this works.

```
http://www.ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6
```

Luke

---

### Post by Rumpty on 2007-02-09
Thanks Luke. I tried the two variations suggested, but unfortunately neither worked. Noticed that the relevant alias line had already been commented out anyway.

---

### Post by Rumpty on 2007-02-09
All sorted out now, thanks to a post by Python from Jan 2005

[http://ubuntuforums.org/showthread.php?t=11544](http://ubuntuforums.org/showthread.php?t=11544)

Something to do with the DSL-504T modem/router not handling IPv6 mapped addresses?

---

