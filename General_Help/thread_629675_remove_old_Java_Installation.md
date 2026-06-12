---
title: "remove old Java Installation"
date: 2007-12-02
forum: General Help
---

### Post by cccc on 2007-12-02
hi

I've updated dapper to gutsy.

howto remove the old Java Installation j2re1.5-sun using **apt-get remove** ?
```

# sudo update-alternatives --config java

Jest 5 alternatyw dostarczaj&#261;cych `java'.

  Wybór        Alternatywa
-----------------------------------------------
          1    /usr/lib/j2re1.5-sun/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.1
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java
*         5    /usr/lib/jvm/java-6-sun/jre/bin/java
```

---

### Post by cccc on 2007-12-02
I solved this problem:
```

# dpkg -l sun-j2re\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nazwa                     Wersja                    Opis
+++-=========================-=========================-==================================================================
ii  sun-j2re1.5               1.5.0+update12            Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
un  sun-j2re1.5debian         <brak>                    (brak dost&#281;pnego opisu)

# apt-get remove --purge sun-j2re1.5

```

---

### Post by barrybevel on 2008-03-04
Thanks for posting soultion.. I found both commands very useful :)

---

