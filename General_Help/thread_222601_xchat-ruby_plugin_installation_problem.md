---
title: "xchat-ruby plugin installation problem"
date: 2006-07-25
forum: General Help
---

### Post by dsfred on 2006-07-25
Hey

I'm trying to install the xchat-ruby plugin ([http://xchat-ruby.sourceforge.net/](http://xchat-ruby.sourceforge.net/)) but when i do "make" i get this:
```
$ make
gcc -L`ruby -rrbconfig -e "puts Config::CONFIG['archdir']"` -g -Wall -O1 -shared -o xchat-ruby.so xchat-ruby.o -lruby
/usr/bin/ld: cannot find -lruby
collect2: ld gaf exit-status 1 terug
make: *** [xchat-ruby.so] Fout 1
```

anyone an idea which extra ruby package i need to install?

thx on advance

---

