---
title: "How can I import .ics from command line with google calendar?"
date: 2013-10-12
forum: General Help
---

### Post by CkDGTAT on 2013-10-12
Hi,

I tried gcalcli but have no clue what is happening. Any alternative?

```


 gcalcli import network-activity-and-plasticity.ics
Traceback (most recent call last):
  File /usr/bin/gcalcli, line 1524, in <module>
    BowChickaWowWow()
  File /usr/bin/gcalcli, line 1292, in BowChickaWowWow
    cfg = LoadConfig(configFile)
  File /usr/bin/gcalcli, line 1174, in LoadConfig
    config.read(os.path.expanduser(configFile))
  File /usr/lib/python2.7/ConfigParser.py, line 305, in read
    self._read(fp, filename)
  File /usr/lib/python2.7/ConfigParser.py, line 512, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/jean/.gcalclirc, line: 1
'              [gcalcli]
'
Thank you

```

---

