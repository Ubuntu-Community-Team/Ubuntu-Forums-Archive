---
title: "ssh and X tunnelling error"
date: 2007-06-01
forum: General Help
---

### Post by .matteo on 2007-06-01
Hi all!

every day I connect to my university server via ssh and X tunnelling to use some applications; since now, every time I connect I've to wait a lot and every program ends with this log error:

> 
IO Error 32 (Broken pipe) on Display "localhost:10.0"
\o (ddserv) library manager exited with status: -111


I use the command

> ssh -XC <server>

can you help me understand why?

thanks ;)

---

### Post by Ek0nomik on 2007-06-04
Why do you use the -C flag?

Could it be that it needs a library file on your local machine?  I am not actually sure how ssh handles needed library files.

---

