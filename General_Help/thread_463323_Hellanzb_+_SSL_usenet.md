---
title: "Hellanzb + SSL usenet"
date: 2007-06-03
forum: General Help
---

### Post by taddy_porter on 2007-06-03
Is this possible? Whenever I configure the SSL connection to newsgroups hellanzb 0.13 will get the amount of download and put in the queue but won't actually download anything. Is there a workaround?

---

### Post by yabbadabbadont on 2007-06-03
Configure Hellanzb to use a normal connection, then install and configure stunnel4 to provide the SSL connection for nntps.

[http://ubuntuforums.org/showpost.php?p=2136276&postcount=6](http://ubuntuforums.org/showpost.php?p=2136276&postcount=6)
and
[http://ubuntuforums.org/showthread.php?t=169749](http://ubuntuforums.org/showthread.php?t=169749)

---

### Post by robertpolson on 2007-06-03
SSL works fin for me.

Check your newsgroup server that it uses correct port for SSL to work, maybe other than 119

---

### Post by clockwork on 2007-09-11
I had the same problem. Hellanzb wont say "I cant connect" or anything similar unless you turn on debugging. Most likely your running into a port issue. Most every usenet provider runs ssl on a different port than regular traffic (try the common ssl port of 443).

Also worth a note is that both of those howto's are out of date since hellanzb now natively supports ssl.

---

### Post by diebels on 2007-09-27
Thanks! Port 443 did the trick.

---

### Post by dimedragger on 2007-10-18
I have tried to set this up and it just sits there when I change my server information to the SSL server.  Also if I change the SSL = False to SSL= True in the hellanzb.conf file it fails. When I run hellanzb in debug mode it just states connection made, then connection lost and then retries.

---

### Post by kditty on 2007-10-24
when i use the settings, and set ssl = True i get:

hellanzb v0.13 (config = /etc/hellanzb.conf)
Unable to use SSL for server: uns
pyOpenSSL is not installed: No module named OpenSSL

---

### Post by diskjunky on 2007-10-25
Hi there i had similar problems when trying to use ssl in hellanzb. 
The package you need to install is python-pyopenssl you can find this in synaptic or you can type 

sudo apt-get install python-pyopenssl

Hope this helps:)

---

### Post by dimedragger on 2007-10-25
> **diskjunky said:**
> Hi there i had similar problems when trying to use ssl in hellanzb. 
The package you need to install is python-pyopenssl you can find this in synaptic or you can type 

sudo apt-get install python-pyopenssl

Hope this helps:)

You just made my day.  Thank you, works like a charm!

---

### Post by sauce214 on 2008-02-20
Thank you, it worked for me as well.

---

### Post by BassKozz on 2008-03-12
> **yabbadabbadont said:**
> then install and configure stunnel4 to provide the SSL connection for nntps.

[http://ubuntuforums.org/showpost.php?p=2136276&postcount=6](http://ubuntuforums.org/showpost.php?p=2136276&postcount=6)
Is this a necessary step? 
I thought hellanzb handles SSL now w/out the need for stunnel.
- - -
I just switched my Usenet provider plan to support SSL so I want to take advantage of it, but I can't get SSL to work, I did **diskjunky**'s recommendation and installed ***python-pyopenssl*** but I am still having trouble getting it to work...
here is what my debug log looks like:
```

2008-03-12 22:45:57,005 [-] Log opened.
2008-03-12 22:45:57,008 hellanzb v0.13 (config = /usr/etc/hellanzb.conf)
2008-03-12 22:45:57,011 [-] twisted.web.server.Site starting on 8760
2008-03-12 22:45:57,012 [-] Starting factory <twisted.web.server.Site instance at 0x881a7ec>
2008-03-12 22:45:57,119 Using: Twisted-2.5.0, TwistedWeb-0.7.0
2008-03-12 22:45:57,120 python: 2.5.1 (r251:54863, Mar  7 2008, 04:10:12) 
2008-03-12 22:45:57,121 [GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)]
2008-03-12 22:45:57,121 os: Linux-2.6.22-14-generic (i686)
2008-03-12 22:45:57,124 initFillServers: fillserver support disabled
2008-03-12 22:45:57,126 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:57,127 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:57,230 recoverStateFromDisk recovered: RecoveredState: version: 0.13 newzbinCookie keys: []
downloading: {u'Beginning Ubuntu Linux From Novice To Professional': {u'category': u'Books', u'totalBytes': u'24053253', u'id': 0, u'name': u'Beginning Ubuntu Linux From Novice To Professional'}}
processing: {}
queued: {u'Ubuntu Linux Toolbox: 1000+ Commands For Ubuntu and Debian Power Users': {u'category': u'Books', u'totalBytes': u'2340719', 'order': 0, u'id': 1, u'name': u'Ubuntu Linux Toolbox: 1000+ Commands For Ubuntu and Debian Power Users '}}
2008-03-12 22:45:57,656 stdinEchoOff - OFF
2008-03-12 22:45:57,717 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:57,720 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:57,723 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:57,816 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,819 NewsHostin[4] CONNECTION MADE
2008-03-12 22:45:57,823 NewsHostin[5] CONNECTION MADE
2008-03-12 22:45:57,827 NewsHostin[6] CONNECTION MADE
2008-03-12 22:45:57,831 NewsHostin[4] CONNECTION LOST
2008-03-12 22:45:57,832 NewsHostin[4] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,834 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bdec> will retry in 1 seconds
2008-03-12 22:45:57,836 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:57,837 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,838 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bb0c> will retry in 3 seconds
2008-03-12 22:45:57,840 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,841 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,842 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b84c> will retry in 4 seconds
2008-03-12 22:45:57,846 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,848 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:57,849 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,850 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b9ac> will retry in 10 seconds
2008-03-12 22:45:57,852 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:57,853 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,866 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bc6c> will retry in 16 seconds
2008-03-12 22:45:57,869 NewsHostin[6] CONNECTION LOST
2008-03-12 22:45:57,870 NewsHostin[6] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,871 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896328c> will retry in 18 seconds
2008-03-12 22:45:57,873 NewsHostin[5] CONNECTION LOST
2008-03-12 22:45:57,875 NewsHostin[5] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,876 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bf6c> will retry in 22 seconds
2008-03-12 22:45:57,878 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,879 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,880 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896310c> will retry in 41 seconds
2008-03-12 22:45:57,890 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,893 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,894 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,895 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896344c> will retry in 76 seconds
2008-03-12 22:45:57,915 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,952 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,953 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,954 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896360c> will retry in 135 seconds
2008-03-12 22:45:57,959 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,963 NewsHostin[5] CONNECTION MADE
2008-03-12 22:45:57,966 NewsHostin[6] CONNECTION MADE
2008-03-12 22:45:57,969 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:57,973 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:57,976 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,977 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,978 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89637cc> will retry in 112 seconds
2008-03-12 22:45:57,980 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,983 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:58,018 NewsHostin[5] CONNECTION LOST
2008-03-12 22:45:58,019 NewsHostin[5] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,020 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963d0c> will retry in 117 seconds
2008-03-12 22:45:58,022 NewsHostin[6] CONNECTION LOST
2008-03-12 22:45:58,023 NewsHostin[6] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,024 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896398c> will retry in 146 seconds
2008-03-12 22:45:58,028 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:58,028 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,029 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963b4c> will retry in 122 seconds
2008-03-12 22:45:58,031 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:58,032 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,033 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896726c> will retry in 103 seconds
2008-03-12 22:45:58,035 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:58,036 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,038 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963ecc> will retry in 71 seconds
2008-03-12 22:45:58,040 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:58,041 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,042 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89670ac> will retry in 133 seconds
2008-03-12 22:45:58,053 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:58,059 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:58,064 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:58,076 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:58,077 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,116 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89675ec> will retry in 104 seconds
2008-03-12 22:45:58,118 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:58,119 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,120 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89677ac> will retry in 117 seconds
2008-03-12 22:45:58,122 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:58,123 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,124 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896742c> will retry in 125 seconds
2008-03-12 22:45:58,124 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:58,125 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:59,514 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:59,515 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:59,552 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:59,573 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:59,574 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:59,575 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bdec> will retry in 116 seconds
2008-03-12 22:45:59,576 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:59,577 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:00,950 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:00,951 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:00,992 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:01,015 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:01,016 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:01,017 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bb0c> will retry in 108 seconds
2008-03-12 22:46:01,018 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:01,019 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:02,790 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:02,791 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:02,823 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:02,849 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:02,850 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:02,851 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b84c> will retry in 116 seconds
2008-03-12 22:46:02,852 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:02,853 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:08,258 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:08,259 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:08,292 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:08,314 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:08,314 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:08,315 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b9ac> will retry in 147 seconds
2008-03-12 22:46:08,316 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:08,317 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:13,350 [twisted.web.server.Site] (Port 8760 Closed)
2008-03-12 22:46:13,351 [twisted.web.server.Site] Stopping factory <twisted.web.server.Site instance at 0x881a7ec>

```
I Assume the: 
**lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]]** 
lines have something to do with it... but what does this mean and how can I fix?

---

### Post by BassKozz on 2008-03-16
Figured it out, I had to set the host to port 563 ](*,)

---

### Post by nfox on 2008-03-17
Didn't work for me...

I have it configured but it says it's accepting connections from 127.0.0.1:VARIOUS PORTS and then it throws a "Connection Reset 0 bytes sent" error.


I can not figure this out. Any ideas? I even disabled my firewall in case.

---

### Post by BassKozz on 2008-03-18
> **nfox said:**
> Didn't work for me...

I have it configured but it says it's accepting connections from 127.0.0.1:VARIOUS PORTS and then it throws a "Connection Reset 0 bytes sent" error.

I can not figure this out. Any ideas? I even disabled my firewall in case.
Can you post your debug log? (remember to wrap [code] tags around it because it gets very long very fast)
Also who is your usenet provider? Which plan are you using w/ that provider?

---

