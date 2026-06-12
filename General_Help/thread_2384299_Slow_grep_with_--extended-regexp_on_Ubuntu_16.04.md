---
title: "Slow grep with --extended-regexp on Ubuntu 16.04"
date: 2018-02-05
forum: General Help
---

### Post by brian-bird on 2018-02-05
I've noticed that since upgrading to Ubuntu 16.04 from Ubuntu 14.04 some regular expression greps seem to be much slower.


For example, on Ubuntu 14.04:
```
# openssl rand -out /tmp/random.txt -base64 100000000; time grep --extended-regexp "[0-9]{10}$" /tmp/random.txt


real    0m0.513s
user    0m0.474s
sys     0m0.036s
```


```
# openssl rand -out /tmp/random.txt -base64 100000000; time grep --perl-regexp "[0-9]{10}$" /tmp/random.txt

real    0m1.017s
user    0m0.989s
sys     0m0.020s
```




However on Ubuntu 16.04:
```
# openssl rand -out /tmp/random.txt -base64 100000000; time grep --extended-regexp "[0-9]{10}$" /tmp/random.txt

real    0m20.619s
user    0m20.587s
sys     0m0.028s
```

```
# openssl rand -out /tmp/random.txt -base64 100000000; time grep --perl-regexp "[0-9]{10}$" /tmp/random.txt

real    0m1.501s
user    0m1.472s
sys     0m0.028s
```







The perl-regex option is a tiny bit slower (and could be due to the randomness in the file). However, the extended-regexp option is consistently ~10x slower on Ubuntu 16.04 than on 14.04. This happens on a fresh install too and using the same hardware.




Q. Could anyone verify if this happens for them too?
Q. Does anyone have any ideas on how to speed up these on Ubuntu 16.04? I have lots of scripts that use "grep -E" and I don't really want to have to change them all to "grep -P" :)


Some details:
Ubuntu 14:
```
# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"

# dpkg -l | grep pcre
ii  libpcre3:amd64                       1:8.31-2ubuntu2.3                          amd64        Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcre3-dev:amd64                   1:8.31-2ubuntu2.3                          amd64        Perl 5 Compatible Regular Expression Library - development files
ii  libpcrecpp0:amd64                    1:8.31-2ubuntu2.3                          amd64        Perl 5 Compatible Regular Expression Library - C++ runtime files
```

Ubuntu 16:
```
# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
# dpkg -l | grep pcre
ii  libpcre16-3:amd64                   2:8.38-3.1                                 amd64        Perl 5 Compatible Regular Expression Library - 16 bit runtime files
ii  libpcre3:amd64                      2:8.38-3.1                                 amd64        Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcre3-dev:amd64                  2:8.38-3.1                                 amd64        Perl 5 Compatible Regular Expression Library - development files
ii  libpcre32-3:amd64                   2:8.38-3.1                                 amd64        Perl 5 Compatible Regular Expression Library - 32 bit runtime files
ii  libpcrecpp0v5:amd64                 2:8.38-3.1                                 amd64        Perl 5 Compatible Regular Expression Library - C++ runtime files
```

---

### Post by TheFu on 2018-02-05
Is grep the issue? [http://manpages.ubuntu.com/manpages/xenial/man1/dieharder.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/dieharder.1.html)
Random number creation is always being improved.

---

