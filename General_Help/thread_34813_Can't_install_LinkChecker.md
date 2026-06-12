---
title: "Can't install LinkChecker"
date: 2005-05-16
forum: General Help
---

### Post by jdonnell on 2005-05-16
I'm trying to install LinkChecker which is a python script and I get this error.
```

error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

```

---

### Post by syltty on 2005-05-16
```
 $ apt-file search /usr/lib/python2.4/config/Makefile
python2.4-dev: usr/lib/python2.4/config/Makefile
python2.4-dev: usr/lib/python2.4/config/Makefile
python2.4-dev: usr/lib/python2.4/config/Makefile

``` 

try if 
sudo apt-get install python2.4-dev
helps

---

### Post by jdonnell on 2005-05-16
Thanks, I found that right after I posted. For some reason I thought the output from apt-search was in alphabetical order and when I looked for the dev package originally I didn't see it.  oops  ](*,)

---

