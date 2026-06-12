---
title: "Missing python module, unable to install it."
date: 2018-02-11
forum: General Help
---

### Post by isprins on 2018-02-11
python replaceWithOsm.py del.osm del2.osm --import:areaTraceback (most recent call last):
  File "replaceWithOsm.py", line 11, in <module>
    from misc import reverseWay
ImportError: No module named misc.
I have tried pip install misc, but that did not work.

The script I am trying to run is located here:
[https://github.com/tibnor/kartverket2osm](https://github.com/tibnor/kartverket2osm)

---

### Post by dragonfly41 on 2018-02-11
I don't know about that script but perhaps you need to install scipy.misc?
I would search around for dependencies.

[Later edit]

Found this ...

[https://downloads.pf.itd.nrl.navy.mil/docs/core/core-python-html/core.misc.html](https://downloads.pf.itd.nrl.navy.mil/docs/core/core-python-html/core.misc.html)

---

### Post by isprins on 2018-02-11
I have these packages installed with apt:
Python-scipy,python-sciscipy,python3-scipy.
Still the same error.
My python version is:
Python 2.7.12
Also tried:
pip install scipy.misc
Collecting scipy.misc
  Could not find a version that satisfies the requirement scipy.misc (from versions: )
No matching distribution found for scipy.misc

---

### Post by again? on 2018-02-11
I'm just starting out to teach myself some python and confess to not knowing much 
about how to run this sort of git download or python in general, but misc.py seems to be included.
ie
/kartverket2osm/src/misc.py

If I copy "replaceWithOsm.py" to the same directory as misc.py, the script appears to work but needs some input.
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] cd git**
**[COLOR="#006400"]glen@Xubarty:~/git$[/COLOR] git clone https://github.com/tibnor/kartverket2osm.git**
Cloning into 'kartverket2osm'...
remote: Counting objects: 260, done.
remote: Total 260 (delta 0), reused 0 (delta 0), pack-reused 260
Receiving objects: 100% (260/260), 75.39 KiB | 116.00 KiB/s, done.
Resolving deltas: 100% (159/159), done.

**[COLOR="#006400"]glen@Xubarty:~/git$[/COLOR] cd kartverket2osm**
**[COLOR="#006400"]glen@Xubarty:~/git/kartverket2osm$[/COLOR] python replaceWithOsm.py**
Traceback (most recent call last):
  File "replaceWithOsm.py", line 11, in <module>
    from misc import reverseWay
ImportError: No module named misc

**[COLOR="#006400"]glen@Xubarty:~/git/kartverket2osm$[/COLOR] cp replaceWithOsm.py src**
**[COLOR="#006400"]glen@Xubarty:~/git/kartverket2osm$[/COLOR] cd src**
**[COLOR="#006400"]glen@Xubarty:~/git/kartverket2osm/src$[/COLOR] python replaceWithOsm.py **
The script requires at least two inputs:
Usage:
python replaceWithOsm.py inputFile outPutfile [--import:water] [--import:area] [--import:all] 

```

---

