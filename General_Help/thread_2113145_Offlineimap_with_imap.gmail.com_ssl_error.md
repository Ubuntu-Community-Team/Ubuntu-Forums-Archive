---
title: "Offlineimap with imap.gmail.com: ssl error"
date: 2013-02-06
forum: General Help
---

### Post by juju43 on 2013-02-06
Hello,

I'm using offlineimap for a long time to backup my gmail and it seems it fails starting recently.

The log is
```

This is OfflineIMAP 6.2.0
Python: 2.5.4 (r254:67916, Aug  9 2010, 08:57:51) 
[GCC 4.2.1 20070719 ]
Platform: openbsd4
Args: ['/usr/local/bin/offlineimap', '-l', '/var/tmp/gmail-backup.sh.log', '-d', 'imap', '-1']
MainThread: OfflineIMAP 6.2.0
Copyright (C) 2002 - 2009 John Goerzen <jgoerzen@complete.org>
This software comes with ABSOLUTELY NO WARRANTY; see the file
COPYING for details.  This is free software, and you are welcome
to distribute it under the conditions laid out in COPYING.
MainThread: Now debugging for imap: IMAP protocol debugging
Account sync gmail: ***** Processing account gmail
Account sync gmail: Copying folder structure from Gmail to Maildir
Account sync gmail: Establishing connection to imap.gmail.com:993.
MainThread: Thread 'Account sync gmail' terminated with exception:
Traceback (most recent call last):
  File "/usr/local/lib/python2.5/site-packages/offlineimap/threadutil.py", line 149, in run
    Thread.run(self)
  File "/usr/local/lib/python2.5/threading.py", line 446, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/local/lib/python2.5/site-packages/offlineimap/accounts.py", line 183, in syncrunner
    self.sync(siglistener)
  File "/usr/local/lib/python2.5/site-packages/offlineimap/accounts.py", line 220, in sync
    remoterepos.syncfoldersto(localrepos, [statusrepos])
  File "/usr/local/lib/python2.5/site-packages/offlineimap/repository/Base.py", line 135, in syncfoldersto
    srcfolders = src.getfolders()
  File "/usr/local/lib/python2.5/site-packages/offlineimap/repository/IMAP.py", line 214, in getfolders
    imapobj = self.imapserver.acquireconnection()
  File "/usr/local/lib/python2.5/site-packages/offlineimap/imapserver.py", line 259, in acquireconnection
    self.sslclientkey, self.sslclientcert)
  File "/usr/local/lib/python2.5/imaplib.py", line 1128, in __init__
    IMAP4.__init__(self, host, port)
  File "/usr/local/lib/python2.5/imaplib.py", line 163, in __init__
    self.open(host, port)
  File "/usr/local/lib/python2.5/site-packages/offlineimap/imapserver.py", line 85, in open
    imaplibutil.new_open_ssl(self, host, port)
  File "/usr/local/lib/python2.5/site-packages/offlineimap/imaplibutil.py", line 171, in new_open_ssl
    raise socket.error(last_error)
error: 65


Last 1 debug messages logged for Account sync gmail prior to exception:
maildir: MaildirRepository initialized, sep is '.'

```it seems to be an ssl error but I can't manage to connect to check certificate

```
$ openssl s_client -showcerts -connect imap.gmail.com:993 2>&1 |tee /tmp/ssl.log


connect: No route to host
connect:errno=9

```Any hints on what's happening ?

Thanks

---

