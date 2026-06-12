---
title: "Python + Apache"
date: 2005-10-17
forum: General Help
---

### Post by A.I. BOT on 2005-10-17
Ok I have edited apache2.conf

and added:

<Directory /var/www/apache2-default/>
        AddHandler mod_python .py
        PythonHandler mptest
        PythonDebug On
</Directory>

then i did:
whammy@double-whammy:/etc/apache2$ sudo pkill -9 apache
whammy@double-whammy:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting web server (Apache2)...                                      [ ok ]

script:

#!/usr/bin/env python
from mod_python import apache

def handler(req):
	req.write("Hello World!")
	return apache.OK

all it does is show me that text above it dosent run it as a script :/

help. tnx

---

### Post by kambizkamrani on 2008-06-22
I'm having this problem with Ubuntu 8.04. Did you end up resolving this problem? If so how, how? Also can anyone else throw out some pointers?

---

