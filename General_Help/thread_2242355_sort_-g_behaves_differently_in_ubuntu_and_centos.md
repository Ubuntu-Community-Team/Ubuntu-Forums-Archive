---
title: "sort -g behaves differently in ubuntu and centos"
date: 2014-09-01
forum: General Help
---

### Post by dieter-erich on 2014-09-01
Hi, I am trying to sort numbers containing scientific notation with "sort -g". I can do it in Centos6.4 but not in ubuntu 14.04. Is this a bug and if not what is the way out?
Thanks, D-E

(wrong) result in ubuntu:              

0.001122
0.001442
0.001442
0.001763
0.001873
0.002084
0.002564
0.002592
0.002885
0.003205
0.007103
0.007939
0.010892
0.011111
0.015868
0.030481
0.042649
0.063937
0.785041
4.808110e-04
6.409025e-04
6.409450e-04
6.410397e-04
8.012506e-04
8.012982e-04


(right) result in Centos:

4.808110e-04
6.409025e-04
6.409450e-04
6.410397e-04
8.012506e-04
8.012982e-04
0.001122
0.001442
0.001442
0.001763
0.001873
0.002084
0.002564
0.002592
0.002885
0.003205
0.007103
0.007939
0.010892
0.011111
0.015868
0.030481
0.042649
0.063937
0.785041

---

### Post by steeldriver on 2014-09-01
What are your locales on the two systems (in particular, LC_COLLATE)?

---

### Post by dieter-erich on 2014-09-02
LC_COLLATE is not set (on neither system)! However, Ubuntu is German, Centos is English. Can this be the reason? And if, how can it be fixed? Thanks!

---

### Post by steeldriver on 2014-09-02
You should be able to check whether locale is the issue by overriding it e.g.

```

LC_ALL=C sort -g yourfile

```

or 
```

export LC_ALL=C
sort -g yourfile

```

(you could also try LC_ALL=POSIX)

---

### Post by sisco311 on 2014-09-02
> **dieter-erich said:**
> However, Ubuntu is German, Centos is English. Can this be the reason?

 Yes, in Germany a comma `,' is used as the decimal mark. ;)

```

root@acme:~# cat num
6.410397e-04
0.015868
0.042649
4.808110e-04
6.409450e-04
0.063937
root@acme:~# cat num.de
6,410397e-04
0,015868
0,042649
4,808110e-04
6,409450e-04
0,063937
root@acme:~# LC_NUMERIC=C sort -g num
4.808110e-04
6.409450e-04
6.410397e-04
0.015868
0.042649
0.063937
root@acme:~# LC_NUMERIC=de_DE.UTF-8 sort -g num
0.015868
0.042649
0.063937
4.808110e-04
6.409450e-04
6.410397e-04
root@acme:~# LC_NUMERIC=C sort -g num.de
0,015868
0,042649
0,063937
4,808110e-04
6,409450e-04
6,410397e-04
root@acme:~# LC_NUMERIC=de_DE.UTF-8 sort -g num.de
4,808110e-04
6,409450e-04
6,410397e-04
0,015868
0,042649
0,063937


```

> **dieter-erich said:**
> And if, how can it be fixed? Thanks!

LC_NUMERIC defines how you format your numbers. You can set LC_NUMERIC to a locale which uses a dot `.' as the decimal mark, for example C,  POSIX or en_GB.UTF-8

Check out: [uhelp]community/Locale[/uhelp]

---

### Post by dieter-erich on 2014-09-03
Thanks a lot, "LC_ALL=C" and the other ways of setting it did the job!

---

