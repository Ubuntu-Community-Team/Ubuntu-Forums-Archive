---
title: "Perl / Apache - undefined symbol: Perl_Top_ptr"
date: 2014-02-21
forum: General Help
---

### Post by lrowens on 2014-02-21
I'm using Ubuntu 13.10.  

I compiled Apache 2.2.26 because of requirements at my workplace.  Upon start, it's giving me:

```
Cannot load httpd/modules/mod_perl.so into server: libperl.so: cannot open shared object file: No such file or directory
```

So I installed the lib:

```
sudo apt-get install libperl-dev
```

Upon retesting, I get the following error:  

```
Cannot load httpd/modules/mod_perl.so into server: httpd/modules/mod_perl.so: undefined symbol: Perl_Top_ptr
```

Is this because the version of apache2 in the Saucy repo is 2.4, not 2.2?

How can I resolve this?

---

### Post by lrowens on 2014-02-21
I compiled mod_perl from source to fix it.

---

