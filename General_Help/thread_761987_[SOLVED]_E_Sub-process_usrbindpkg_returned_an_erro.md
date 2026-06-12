---
title: "[SOLVED] E: Sub-process /usr/bin/dpkg returned an error cod"
date: 2008-04-21
forum: General Help
---

### Post by Bobrm2 on 2008-04-21
I have tried to install then gave up an now attempting to uninstall the python-poker-net. Could someone help, and I think that the subject line is probably a key to the problem. Thanks in advance

   I Traceback (most recent call last):
  File "/usr/sbin/pokerconfigupgrade", line 121, in <module>
    sys.exit(main())
  File "/usr/sbin/pokerconfigupgrade", line 103, in main
    config.load(file)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokernetworkconfig.py", line 46, in load
    status = pokerengineconfig.Config.load(self, path)
  File "/usr/lib/python2.5/site-packages/pokerengine/pokerengineconfig.py", line 69, in load
    self.doc = libxml2.parseFile(self.path)
  File "/var/lib/python-support/python2.5/libxml2.py", line 1280, in parseFile
    if ret is None:raise parserError('xmlParseFile() failed')
libxml2.parserError: xmlParseFile() failed
dpkg: error processing python-poker-network (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python-poker-network
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bobrm2 on 2008-05-18
Upgrade to Hardy Heron solved the problem(?), what ever it was.

---

