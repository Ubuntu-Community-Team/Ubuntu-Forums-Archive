---
title: "HTK &amp; Julius : perl script uses all RAM"
date: 2013-07-01
forum: General Help
---

### Post by doomOo7 on 2013-07-01
Hello,
I am currently in the process of building an acoustic model for the TIMIT corpus, with HTK, in order to use it with Julius (speech recognition software).
However, I have a problem when using the slf2dfa.sh script, found on the Julius page : [http://julius.sourceforge.jp/en_index.php](http://julius.sourceforge.jp/en_index.php) (search slg2dfa, they made a typo) to convert the grammar to the Julius format.

My grammar on HTK format is about 1 megabyte.
After the first phase of slf2dfa, a call to "remove_null.pl", a 900 megabytes file is generated (which seems quite a lot).
The second phase, "moore2mealy.pl" never finish : the process is killed by the linux out-of-memory killer before, because it fills the RAM. (And I have tested on a computer with 64 gigabytes of RAM!).

I made a python script to automate the building of the corpus, so I share it here, in attachment.
If you want to test you have to copy the TIMIT dir in the directory of the scripts so that it looks like : 

```

~/model/timit2htk.py
......../configuration.py
......../CORRECTED_TIMITDIC.TXT
......../TIMIT/TRAIN
......../TIMIT/TRAIN/DR1/etc...
......../TIMIT/TEST

```

and run timit2htk.py
It's still a work in progress, still.
The grammar is generated from the dictionary using the bigram method (I think), wtih HLStats and HBuild.


Thanks everybody, and please if this is the wrong section may a moderator move it ? I first planned to put it in Assistive technology but I am not sure it really is the case...

EDIT : forgot attachment
[ATTACH]244312[/ATTACH]

---

### Post by doomOo7 on 2013-07-04
Bump ?

---

