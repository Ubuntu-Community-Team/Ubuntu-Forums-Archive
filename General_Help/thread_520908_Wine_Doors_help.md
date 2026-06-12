---
title: "Wine Doors help"
date: 2007-08-08
forum: General Help
---

### Post by Swarms on 2007-08-08
Hey, after I have installed wine-doors, and try to launch it through the terminal, I get this output.

> bear@bear-desktop:~$ wine-doors
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 21, in <module>
    from wine import wine
  File "/usr/share/wine-doors/src/wine.py", line 11, in <module>
    from preferences import preferences
  File "/usr/share/wine-doors/src/preferences.py", line 161, in <module>
    preferences = Preferences()
  File "/usr/share/wine-doors/src/preferences.py", line 48, in __init__
    self.Load()
  File "/usr/share/wine-doors/src/preferences.py", line 128, in Load
    parser.parse( prefsfile )
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 109, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/xmlreader.py", line 125, in parse
    self.close()
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: /home/bear/.wine/wine-doors/preferences.xml:3:0: no element found


---

### Post by UK-Wobbie on 2007-08-08
> **Swarms said:**
> Hey, after I have installed wine-doors, and try to launch it through the terminal, I get this output.

Hey i have not seen that be for.... But i got to say Wine Doors i hate it lmfao I had it installed on my ubuntu 7.40 and wine did not like it when i install stuff from Wine Doors! It f**ked up wine like anything and it did not yet me unstill it :( So i had to restill my ubuntu lol
So FOR YOU ALL DO NOT USE WINE DOORS :)

---

### Post by Swarms on 2007-08-08
Oh well, it was also more for tjecking its potential out, maybe it could be branched with Wine or something, merely guessing.

---

### Post by UK-Wobbie on 2007-08-08
> **Swarms said:**
> Oh well, it was also more for tjecking its potential out, maybe it could be branched with Wine or something, merely guessing.

Can you unstill it? I no it did not yet me unstill... It open the wine doors window but when i instill stuff from that wine did not like it 1 bit lmfao and wine f**ked it self :( Did not open any games or anything!
So can you unstill it ok? And is wine still working? :)

---

### Post by Swarms on 2007-08-08
Yeah wine works great, and nope haven't uninstalled it, want it working instead. :)

---

### Post by UK-Wobbie on 2007-08-08
> **Swarms said:**
> Yeah wine works great, and nope haven't uninstalled it, want it working instead. :)

ok lol :)

---

### Post by Swarms on 2007-08-09
Bump

---

