---
title: "snmptrapd error"
date: 2016-08-12
forum: General Help
---

### Post by sovenko on 2016-08-12
Please help with my problem:

snmptrapd not started:

Error```
dmitry@tv-server1:~$ snmptrapd -f -L o
snmptrapd: symbol lookup error: /usr/lib/x86_64-linux-gnu/libnetsnmptrapd.so.30: undefined symbol: my_progname
```

Version ```
dmitry@tv-server1:~$ apt-cache policy snmpdsnmpd:
  &#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;: 5.7.2~dfsg-8.1ubuntu3.2
  &#1050;&#1072;&#1085;&#1076;&#1080;&#1076;&#1072;&#1090;:   5.7.2~dfsg-8.1ubuntu3.2
  &#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1074;&#1077;&#1088;&#1089;&#1080;&#1081;:
 *** 5.7.2~dfsg-8.1ubuntu3.2 0
        500 http://ru.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     5.7.2~dfsg-8.1ubuntu3.1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     5.7.2~dfsg-8.1ubuntu3 0
        500 http://ru.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages



```

---

