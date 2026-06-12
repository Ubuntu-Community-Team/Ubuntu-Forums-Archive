---
title: "CA Management"
date: 2008-03-19
forum: General Help
---

### Post by SpaceTeddy on 2008-03-19
Hi Everybody, 

this is less a problem that it would be a feature - but i can't seem to find any solution to this that would fit my needs.

Well, here is my problem:
We have a lot of internal servers and network components running that all require SSL certificates on their web-frontends (company policy). So i generated a self signed CA and went on signing the SSL certificates for the webservers with it. This is all pretty straight forward as it boils down to only a few lines in the CLI.
However, i am not the only one working with these, and others need a software or at least something that helps them generate these certificates. So what i essentially needs is a piece of code that will

a) give me a menu driven generation of CA and then SSL Certificates without someone knowing a thing about openssl, CA's or certificates. 

b) give me a webpage that can do this (i can secure that itself with a SSL certificate)

c) a (i am almost afraid to say this) webmin plugin that can handle this task

all of these solution must be capable of generating private keys (and then a request from that) as well as signing a generated request from another source.

if anyone can give me a hint where i could get such a software/plugin it would be really great...

thank you all in advance

---

### Post by SpaceTeddy on 2008-03-30
bump ?

---

