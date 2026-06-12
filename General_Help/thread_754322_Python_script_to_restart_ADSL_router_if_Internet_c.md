---
title: "Python script to restart ADSL router if Internet connection drops"
date: 2008-04-13
forum: General Help
---

### Post by chrismyers on 2008-04-13
Hi guys,

I'm trying to write a python script which will restart my router if it drops the ADSL connection.

I managed to create the following code that sucessfully restarts the ADSL connection:

```


#!/usr/bin/python
import sys, telnetlib
host = '192.168.1.1'
password = 'secret\r'
tn = telnetlib.Telnet(host)
tn.read_until('Password: ')
tn.write(password)
tn.read_until('>')
tn.write('adsl reboot\r')
tn.read_until('>')
tn.close()
```What I need now is to be able to test whether the Internet is available by pinging a site, such as bbc.co.uk.

Does anyone have an example python script that will make this decision depending on ping availability?

Many thanks in advance :)

---

### Post by pointone on 2008-04-13
```
#! /usr/bin/env python

import os

if os.system("ping www.google.com -c 2"):
    print "We're not connected!!!"
else:
    print "Things are fine!"
```

---

### Post by chrismyers on 2008-04-15
Many thanks,

For anyone interested here's the code that works with my Router (Draytek Vigor 2800):

```
#!/usr/bin/python
import sys, telnetlib, os, subprocess

host = '192.168.1.1'
user = '\r'
password = 'secret\r'

if os.system("ping bbc.co.uk -c 2"):
    print "We're not connected!!!"
    tn = telnetlib.Telnet(host)
    tn.read_until('Password: ')
    tn.write(password)
    tn.read_until('>')
    tn.write('adsl reboot\r')
    tn.read_until('>')
    tn.close()
#    I need to put email notification here (after a 2 minute pause).
else:
    print "Things are fine"
    exit
```I realised that I need to put email notification in the script to prove that it is doing its job. I still need to work out how to do this.

Cheers

---

