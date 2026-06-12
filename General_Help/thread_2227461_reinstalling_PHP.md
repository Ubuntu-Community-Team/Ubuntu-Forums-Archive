---
title: "reinstalling PHP"
date: 2014-06-02
forum: General Help
---

### Post by djbaker2 on 2014-06-02
Recently, I wanted to use pthreads, a PHP extension and part of the setup was to compile PHP from source. I would now like to revert to using the version of PHP that Ubuntu package management provides. When I attempt to reinstall PHP using 

[HTML]apt-get install php5[/HTML] 

it completes but my environment php is still using the one that i compiled.

---

### Post by djbaker2 on 2014-06-02
I fixed this. I was actually trying to reinstall php5-cli. I deleted the php executable and it made apt think that php5-cli wasn't installed so reinstalling it worked after that.

---

