---
title: "Difficulty in using wolframalpha API using python in ubuntu"
date: 2014-08-09
forum: General Help
---

### Post by baljeet_singh on 2014-08-09
Hello guys and my seniors...i get a error in using these code:-
please help me to sort this problem

--------------------------------------------------

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import urllib
import wolframalpha
import urllib2
from xml.etree import ElementTree as etree
import sys

appid = '**************'
client = wolframalpha.Client(appid)

query = ' '.join(sys.argv[1:])
res = client.query(query)

if len(res.pods) > 0:
texts = ""
pod = res.pods[1]
if pod.text:
texts = pod.text
else:
texts = "I have no answer for that"
# to skip ascii character in case of error
texts = texts.encode('ascii', 'ignore')
print texts
else:
print "Sorry"

-------------------------------------------------------------------------------------------------
error:-

baljeet@baljeet-System-Product-Name:~$ python qw.py '4 times 3'
Traceback (most recent call last):
File "qw.py", line 11, in <module>
client = wolframalpha.Client(appid)
AttributeError: 'module' object has no attribute 'Client'
-------------------------------------------------------------------------------------------------

---

