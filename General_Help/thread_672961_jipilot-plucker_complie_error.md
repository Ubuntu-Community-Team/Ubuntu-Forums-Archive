---
title: "jipilot-plucker complie error"
date: 2008-01-20
forum: General Help
---

### Post by jan_everts on 2008-01-20
I am trying to complie jpilot-plucker, but getting the following error during make:
plugin.c: In function 'sync_install':
plugin.c:271: error: too few arguments to function 'pi_file_install'
make[2]: *** [plugin.lo] Fout 1
make[2]: Map '/home/jan/jpilot-plucker-0.01/src' wordt verlaten
make[1]: *** [all-recursive] Fout 1
make[1]: Map '/home/jan/jpilot-plucker-0.01' wordt verlaten
make: *** [all] Fout 2

What am i doing wrong and how to solve this. I am just using these directions:
[http://jasonday.home.att.net/code/jpilot-plucker/README]("http://jasonday.home.att.net/code/jpilot-plucker/README")

configure works fine, the problem seems to be line 271 in the source and I can't continue.

---

