---
title: "---What kind of package is it!"
date: 2020-07-01
forum: General Help
---

### Post by bzhao on 2020-07-01
Dear All,

Today I have just done the below commands:

1.  LC_ALL=C  dpkg -l language-pack-zh-base
results printing:
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
un  language-pack-zh-base          <none>               <none>               (no description available)

2.  LC_ALL=C  dpkg -l language-pack-zh-basex
results printings:
dpkg-query: no packages found matching language-pack-zh-basex

3. apt-cache pkgnames |grep  language-pack-zh-base
results printing: (nothing)

So my question is:
What kind of package is the language-pack-base.?   

I have used the XUbuntu 18.04 for about 8 months,  which is is installed from Xubuntu 18.04 iso file

Thanks beforehand !

Bill Z

---

### Post by dino99 on 2020-07-01
This package provides the bulk of translation data and is updated only seldom. language-pack-zh-hans-base provides frequent translation updates

---

### Post by Holger_Gehrke on 2020-07-01
Actually it's a bit more complicated than dino99 writes. The package language-pack-zh-base is a virtual package, other packages provide the capabilities of that package namely language-pack-zh-hans-base for simplified Chinese and language-pack-zh-hant-base for traditional Chinese. There are the *-base packages which contain translations for a lot of programs and which stay the same for a long time and packages without the -base postfix which contain new or changed translations and get updated more frequently.

Holger

---

