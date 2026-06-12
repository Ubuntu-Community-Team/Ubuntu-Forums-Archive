---
title: "Localhost Hangs.."
date: 2007-11-04
forum: General Help
---

### Post by zuccs on 2007-11-04
I had a working LAMP stack, but since mounting my other hard drives on boot, apache2 seems to hang until Firefox gives the "...is taking too long to respond" error message. I am pretty sure I have done nothing else to affect it since then..

I check the apache2 error log and this is what I get:

```
[Sun Nov 04 22:02:40 2007] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Sun Nov 04 22:02:40 2007] [notice] caught SIGWINCH, shutting down gracefully
[Sun Nov 04 22:03:46 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 configured -- resuming normal operations
```

I am pretty sure this is just from me restarting the apache service though...

Any ideas? Thanks in advance...

---

