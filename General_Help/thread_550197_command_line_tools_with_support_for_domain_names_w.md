---
title: "command line tools with support for domain names with unicode characters"
date: 2007-09-13
forum: General Help
---

### Post by leonidas666 on 2007-09-13
I was playing around with some domains with unicode characters (e.g. [www.öäü.de](www.öäü.de)). Since some time there is the IDNA standard, which says that unicode strings should be translated to ascii strings in the client, so that the server don't have to change. This works nicely in firefox, e.g. when i want to see the website [www.bücher.de](www.bücher.de). However, when i try to ping the server, 
```
ping www.bücher.de 
```
it does not work. I have to enter 
```
ping xn--bcher-kva.de
```
So shouldn't ping do the translation from [www.bücher.de](www.bücher.de) to [www.xn--bcher-kva.de](www.xn--bcher-kva.de) by itself? 
I found that other commands, like dig and host also do not conform to IDNA and do not work with unicode domains. Is that actually the intended behaviour?

---

