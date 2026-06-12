---
title: "Cross Tool-NG Build failed"
date: 2014-07-06
forum: General Help
---

### Post by ieatorangezz on 2014-07-06
I'm trying to create an offline wallet for Bitcoin on a raspberry pi, but i first need to cross complile armory. I'm having trouble getting ct-ng to build, can anyone explain why I'm getting this error?


```
/Documents/OS/crosstool-ng-1.19.0$ ./ct-ng build
[INFO ]  Performing some trivial sanity checks
[INFO ]  Build started 20140706.192428
[INFO ]  Building environment variables
[ERROR]   
[ERROR]  >>
[ERROR]  >>  Build failed in step '(top-level)'
[ERROR]  >>
[ERROR]  >>  Error happened in: CT_DoExecLog[scripts/functions@257]
[ERROR]  >>        called from: main[scripts/crosstool-NG.sh@260]
[ERROR]  >>
[ERROR]  >>  For more info on this error, look at the file: 'build.log'
[ERROR]  >>  There is a list of known issues, some with workarounds, in:
[ERROR]  >>      '/opt/cross/share/doc/crosstool-ng/ct-ng.1.19.0/B - Known issues.txt'
[ERROR]   
[ERROR]  (elapsed: 0:00.40)
[00:01] / make: *** [build] Error 1


```

---

### Post by ieatorangezz on 2014-07-06
Still getting the same error, i can't find any answers online. Does anyone have experience with this or know a workaround?

---

