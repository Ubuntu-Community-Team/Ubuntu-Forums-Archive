---
title: "Cannot start Zope instance in Gutsy"
date: 2008-01-12
forum: General Help
---

### Post by bocacorazon on 2008-01-12
I have installed zope2.10 in a fresh Gutsy install.
Zope itself installed without trouble, and the instance creation finished with no issues.
The problem starts when I try to start the new instance.
I get:
```

root@martirio:~#  /etc/init.d/zope2.10 restart
 * Zope2.10: restarting martirio instance                                [fail]

```

I looked all over the /var/log  folder for an explanation but to no avail.
However, if I try:

```

root@martirio:/var/lib/zope2.10/instance/martirio/log# /var/lib/zope2.10/instance/martirio/bin/zopectl start
Traceback (most recent call last):
  File "/usr/lib/zope2.10/lib/python/Zope2/Startup/zopectl.py", line 322, in <module>
    main()
  File "/usr/lib/zope2.10/lib/python/Zope2/Startup/zopectl.py", line 280, in main
    options.realize(args)
  File "/usr/lib/zope2.10/lib/python/Zope2/Startup/zopectl.py", line 91, in realize
    ZDOptions.realize(self, *args, **kw)
  File "/usr/lib/zope2.10/lib/python/zdaemon/zdoptions.py", line 273, in realize
    self.load_schema()
  File "/usr/lib/zope2.10/lib/python/zdaemon/zdoptions.py", line 321, in load_schema
    self.schema = ZConfig.loadSchema(self.schemafile)
  File "/usr/lib/zope2.10/lib/python/ZConfig/loader.py", line 31, in loadSchema
    return SchemaLoader().loadURL(url)
  File "/usr/lib/zope2.10/lib/python/ZConfig/loader.py", line 65, in loadURL
    return self.loadResource(r)
  File "/usr/lib/zope2.10/lib/python/ZConfig/loader.py", line 159, in loadResource
    schema = ZConfig.schema.parseResource(resource, self)
  File "/usr/lib/zope2.10/lib/python/ZConfig/schema.py", line 27, in parseResource
    xml.sax.parse(resource.file, parser)
  File "/usr/lib/zope2.10/lib/python/Zope2/Startup/__init__.py", line 33, in parse
    logger = logging.getLogger("Zope")
  File "xml/sax/expatreader.py", line 107, in parse
  File "xml/sax/xmlreader.py", line 123, in parse
  File "xml/sax/expatreader.py", line 207, in feed
  File "xml/sax/expatreader.py", line 301, in start_element
  File "/usr/lib/zope2.10/lib/python/ZConfig/schema.py", line 99, in startElement
    getattr(self, "start_" + name)(attrs)
  File "/usr/lib/zope2.10/lib/python/ZConfig/schema.py", line 475, in start_schema
    keytype, valuetype, datatype = self.get_sect_typeinfo(attrs)
  File "/usr/lib/zope2.10/lib/python/ZConfig/schema.py", line 201, in get_sect_typeinfo
    datatype = self.get_datatype(attrs, "datatype", "null", base)
  File "/usr/lib/zope2.10/lib/python/ZConfig/schema.py", line 194, in get_datatype
    return self._registry.get(dtname)
  File "/usr/lib/zope2.10/lib/python/ZConfig/datatypes.py", line 398, in get
    t = self.search(name)
  File "/usr/lib/zope2.10/lib/python/ZConfig/datatypes.py", line 423, in search
    package = __import__(n, g, g, component)
  File "/usr/lib/zope2.10/lib/python/Zope2/Startup/datatypes.py", line 20, in <module>
    from ZODB.config import ZODBDatabase
  File "/usr/lib/zope2.10/lib/python/ZODB/__init__.py", line 20, in <module>
    from persistent import TimeStamp
  File "/usr/lib/zope2.10/lib/python/persistent/__init__.py", line 19, in <module>
    from cPersistence import Persistent, GHOST, UPTODATE, CHANGED, STICKY
ImportError: /usr/lib/zope2.10/lib/python/persistent/cPersistence.so: undefined symbol: Py_InitModule4


```

Here's some more data:
```

root@martirio:/var/lib/zope2.10/instance/martirio/log# which python
/usr/bin/python
root@martirio:/var/lib/zope2.10/instance/martirio/log# ls -ltr /usr/bin/python
lrwxrwxrwx 1 root root 9 Jan 11 17:27 /usr/bin/python -> python2.5

```

I noticed that when I installed zope it also installed python2.4. Is this perhaps the issue?
Maybe zope requires 2.4
If so...how do I make zope use 2.4? Ideally I'd do it without making EVERY app use 2.4, but if that is not possible I could live with that (the machine will be mainly a zope server).

Thanks in advance for your help.
Marcos

---

### Post by rowanparker on 2008-01-12
If you try to restart something that isn't running it can sometimes fail.
Are you sure it is running already?
Try running ```
/etc/init.d/zope2.10 start
```

---

### Post by bocacorazon on 2008-01-12
Yes, I tried with the same results.
```

root@martirio:~# /etc/init.d/zope2.10 start
 * Zope2.10: starting martirio instance                                  [fail]

```

---

### Post by bocacorazon on 2008-01-12
Well, I tried changing the python link to python2.4 and it worked.

```

root@martirio:/usr/bin# ls -ltr python
lrwxrwxrwx 1 root root 9 Jan 11 17:27 python -> python2.5
root@martirio:/usr/bin# ln -sf python2.4 python
root@martirio:/usr/bin# ls -ltr python
lrwxrwxrwx 1 root root 9 Jan 12 12:43 python -> python2.4
root@martirio:/usr/bin# /etc/init.d/zope2.10 start
 * Zope2.10: starting martirio instance                                  [ OK ]

```

I wish the zope package handled it a little better. 
Do you think this could be considered a bug?

---

