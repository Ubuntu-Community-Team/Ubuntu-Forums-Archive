---
title: "scheduled daily webpage snapshot"
date: 2008-01-21
forum: General Help
---

### Post by frone on 2008-01-21
Wondering if anyone knows of an easy way to get a scheduled daily snapshot of a webpage.  

- Thanks!

---

### Post by apjone on 2008-01-21
> **frone said:**
> Wondering if anyone knows of an easy way to get a scheduled daily snapshot of a webpage.  

- Thanks!

Depends on what you mean? Is it a single page? if its a single page you could do the following in a script and cron it

#!/bin/bash
filename="thexpgeek" #Put your filename here
url="thexpge.com" #put the url here
dte=` date +%d%m%Y`
output="$filename-$dte.html"
wget $url -O $output

---

### Post by frone on 2008-01-22
Apjone -

Thanks for the info.  I used your script and installed the 'Schedule' app (never used cron before, but will learn it).  It worked exactly as you said.

You are one of the ones that really help this movement keep rolling - keep up the great work with us noobs...

---

