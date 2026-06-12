---
title: "Nethack in console"
date: 2005-10-30
forum: General Help
---

### Post by coldsalmon on 2005-10-30
Hi,

I've been trying forever to get Nethack working in the console (Ctrl + Alt + F1), but I can't seem to get IBM or DEC graphics working.  They both just come out garbled.  I tried using a bunch of differend console fonts, including a cp437 one, but the same thing happens.  Here's a screenshot from X on the xterm, it looks the same as on the console:  [http://www.drew-edwards.com/snapshot1.jpg](http://www.drew-edwards.com/snapshot1.jpg)

I really don't think the font is the problem, since every font looks exactly the same.  Any suggestions would be appreciated.

Thanks,

--C

---

### Post by coldsalmon on 2008-06-14
I solved this a while ago, but never posted it. The problem is with the encoding, not the font. I found a python script a long time ago that solved the problem, but I cannot now locate the author, so I am unfortunately unable to credit it. Here's the script:

```
#!/usr/bin/python -tt
# vim:ts=8:sts=4:sw=4:et:

from subprocess import *
import sys #, codecs
import os

special = {

    # ibm866 is only an approximation of the encoding nethack
    # seems to use; these four correct the errors I know of
    '\xf0': u'\u2261',   # iron bars (identical to, three lines)
    '\xf1': u'\u2663',   # tree (clubs)
    '\xf4': u'\u148b',   # fountain (top half of intergral)
    '\xf7': u'\u2248',   # water/lava (almost equal, double tilde)

    # Some things that are just nice - require the dungeon
    # features to be set accordingly in your .nethackrc
    '\xf2': u'\u2264',   # ladder up (less than or equal)
    '\xf3': u'\u2265',   # ladder down (greater than or equal)
    '\xf5': u'\u2229',   # grave (intersection symbol)

}

# ibm866 = codecs.lookup('ibm866')
# utf8 = codecs.lookup('UTF-8')

handle = Popen(sys.argv[1:], stdout=PIPE, bufsize=1)
buf = handle.stdout.read(1)
while buf != '':
    try:
        if buf in special: out = special[buf]
        else:              out = buf.decode('ibm866')
        sys.stdout.write(out.encode('UTF-8'))
        buf = handle.stdout.read(1)
    except Exception, e:
        os.system('reset')
        raise e
handle.wait()
 
```

You just have to make it executable, then run

```
./ibm.py nethack
```

---

