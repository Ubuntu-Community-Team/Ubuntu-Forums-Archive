---
title: "Odd placement of cgi-bin"
date: 2013-08-22
forum: General Help
---

### Post by bkline on 2013-08-22
Why does Ubuntu put cgi-bin under /usr/lib?  According to the [FHS standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html#THEUSRHIERARCHY") for Linux filesystems:

> /usr is the second major section of the filesystem. /usr is shareable, read-only data. That means that /usr should be shareable between various FHS-compliant hosts and must not be written to. Any information that is host-specific or varies with time is stored elsewhere.

Ubuntu puts the static pages for web servers in the right place (/var/www); why not the dynamic pages?

---

