---
title: "hellanzb  Issue Not downloading anything"
date: 2007-08-09
forum: General Help
---

### Post by cafu on 2007-08-09
I have installed hellanzb 0.13  & I can't get it to download anything.  I edited the config file with my server info, I placed a .nzb file in .queue dir, load up the program (hellanzb.py . The i get this

hellanzb v0.13 (config = /usr/etc/hellanzb.conf)
(usenet) Opening 4 connections...
hellanzb - Now monitoring queue...
Resuming: Microsoft_Windows_XP_SP3_Build_3180
Parsing: msgid_2600279_Microsoft_Windows_XP_SP3_Build_3180.nzb...
Parsed: 35 files (1604 posts), 389.2MB
Queued: 389.2MB
[1]
[2]
[3]
[4]
[Total] 0.0KB/s, 389 MB queued, ETA: 00:00:00

It shows the nzb correctly... but it does not download anything! the ETA in yellow stays to 0.00 forever!, i can connect to the server with pan or klibido, anyhelp on this issue, here is my config file


defineServer(id = 'usenet',
             hosts = [ 'news.usenet.net:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'xxxx',
             password = 'xxxxx',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = '/home/cafu/'

---

### Post by jupiter2006 on 2007-08-12
This is most likely because of wrong server info. (host_name : port_number, username, password) in the config file.  

Make sure that you're entering your username/password correctly. Also make sure that you're editing the right conf. file (your setup shows that it is the one located at /usr/etc/hellanzb.conf instead of the default location in newer versions)

---

### Post by dimedragger on 2007-10-03
nm, i fixed it.

---

### Post by mattyp1 on 2007-11-23
Do you mind sharing what you did. I am having the same problem. Doesn't seem to have anything to do with username and password :(

Thanks

---

### Post by icedfusion on 2007-12-28
I have been using hellanzb for a while now, I recently did an update and restarted my pc and now hellanzb will not download anything...it just sits there and i get the following in the debug-log:

Any ideas? the debug-log output seems pretty useless in my opinion.

Cheers.

ice.

```
2007-12-28 21:29:30,308 [-] Log opened.
2007-12-28 21:29:30,311 hellanzb v0.13 (config = /etc/hellanzb.conf)
2007-12-28 21:29:30,313 [-] twisted.web.server.Site starting on 8760
2007-12-28 21:29:30,313 [-] Starting factory <twisted.web.server.Site instance at 0x85f42ac>
2007-12-28 21:29:30,410 Using: Twisted-2.5.0, TwistedWeb-0.7.0
2007-12-28 21:29:30,410 python: 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
2007-12-28 21:29:30,411 [GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)]
2007-12-28 21:29:30,411 os: Linux-2.6.22-14-generic (i686)
2007-12-28 21:29:30,412 initFillServers: fillserver support disabled
2007-12-28 21:29:30,412 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x872790c>
2007-12-28 21:29:30,413 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x8727a2c>
2007-12-28 21:29:30,557 recoverStateFromDisk recovered: RecoveredState: version: 0.13 newzbinCookie keys: []
downloading: {u'Manhunt_2': {u'totalBytes': u'1107367107', u'id': 0, u'name': u'Manhunt_2'}}
processing: {}
queued: {u'Rescue_Dawn_(2006)_(2_CD)': {u'totalBytes': u'1720640704', 'order': 1, u'id': 9, u'name': u'Rescue_Dawn_(2006)_(2_CD)'}, u'Code_Name__The_Cleaner_(2007)': {u'totalBytes': u'809345596', 'order': 0, u'id': 8, u'name': u'Code_Name__The_Cleaner_(2007)'}}
2007-12-28 21:29:31,171 stdinEchoOff - OFF
2007-12-28 21:30:00,414 [-] <twisted.internet.tcp.Connector instance at 0x8727a6c> will retry in 1 seconds
2007-12-28 21:30:00,415 [-] <twisted.internet.tcp.Connector instance at 0x8727bac> will retry in 2 seconds
2007-12-28 21:30:00,417 [-] <twisted.internet.tcp.Connector instance at 0x8727d0c> will retry in 3 seconds
2007-12-28 21:30:00,418 [-] <twisted.internet.tcp.Connector instance at 0x8727e6c> will retry in 6 seconds
2007-12-28 21:30:00,419 [-] <twisted.internet.tcp.Connector instance at 0x8727fec> will retry in 12 seconds
2007-12-28 21:30:00,420 [-] <twisted.internet.tcp.Connector instance at 0x873018c> will retry in 19 seconds
2007-12-28 21:30:00,421 [-] <twisted.internet.tcp.Connector instance at 0x873030c> will retry in 28 seconds
2007-12-28 21:30:00,422 [-] <twisted.internet.tcp.Connector instance at 0x873048c> will retry in 52 seconds
2007-12-28 21:30:00,423 [-] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x872790c>
2007-12-28 21:30:00,424 [-] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x8727a2c>
2007-12-28 21:30:01,954 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x872790c>
2007-12-28 21:30:01,955 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x8727a2c>
2007-12-28 21:30:31,958 [-] <twisted.internet.tcp.Connector instance at 0x8727a6c> will retry in 101 seconds
2007-12-28 21:30:32,638 [-] <twisted.internet.tcp.Connector instance at 0x8727bac> will retry in 152 seconds
2007-12-28 21:30:34,006 [-] <twisted.internet.tcp.Connector instance at 0x8727d0c> will retry in 98 seconds
2007-12-28 21:30:37,378 [-] <twisted.internet.tcp.Connector instance at 0x8727e6c> will retry in 114 seconds
2007-12-28 21:30:42,638 [-] <twisted.internet.tcp.Connector instance at 0x8727fec> will retry in 104 seconds
2007-12-28 21:30:49,546 [-] <twisted.internet.tcp.Connector instance at 0x873018c> will retry in 118 seconds
2007-12-28 21:30:58,862 [-] <twisted.internet.tcp.Connector instance at 0x873030c> will retry in 148 seconds
2007-12-28 21:31:23,282 [-] <twisted.internet.tcp.Connector instance at 0x873048c> will retry in 112 seconds
2007-12-28 21:31:23,283 [-] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x872790c>
2007-12-28 21:31:23,284 [-] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x8727a2c>
```

---

### Post by mattyp1 on 2007-12-29
That is strange. While I haven't seen this before it does look like a problem with twisted. Have you tried installing/verifying/reinstalling twisted. It is available in the repositories.

---

### Post by icedfusion on 2007-12-29
thanks for the response.

I have tried reinstalling, uninstalling and then reinstalling the python-twisted packages with still no success (i have done the same with hellanzb)
Each time I run hellanzb i still end up with the files queued but no activity.

I know my .conf file is ok as I use it on another machine and hellanzb runs fine.

I am pretty sure it was an auto-update that has caused this - but I don't know how to debug this problem.

Any other tips would be great.


Thanks

ice.

---

### Post by icedfusion on 2007-12-29
any logs I can look at to at least try and fix it myself??

Cheers

ice.

---

### Post by mattyp1 on 2007-12-30
You can enable detailed logging but I think you've already done so. In case you haven't, try launching hellanzb as follows:
"hellanzb.py -d ~/hellanzblog". The results should provide more info.

---

### Post by icedfusion on 2007-12-30
Thanks for that. 

I had enabled the debugging in the conf file.

As this machine is currently not my main one (i intend it to be) - I today reinstalled 7.10 from scratch and updated and only installed what was required to run hellanzb.

Unfortunately the outcome is the same - hellanzb fires up but does not make any connections via the 'twisted' links.

to be honest, I am surprised that I am the only person having this problem since the update.

Will trawl around to see if I can find any other info about this.

Cheers

ice.

---

### Post by mattyp1 on 2008-01-01
I am surprised as well. I am not running hellanzb on my ubuntu machine so my experience may be a little different. However, I just rebuilt my Linksys NSLU2 and noticed that hellanzb is not working. I receive a number of odd errors. The only thing I did differently is I installed the py25hellanzb which uses python 2.5. Just a thought but  you could try using python 2.4 instead...

Happy New Year

Peace

---

### Post by Mithrilhall on 2008-01-02
Try chowning (chown) the directory that holds your queued files, temp files, extracted file, etc...

```

chown -Rv username:username /home/username/nzb

```

---

### Post by icedfusion on 2008-01-02
Will give the permissions change a try tonight - would not have thought it would have been a problem as the directories reside in my home dir structure.

As to using python 2.4 - How do i downgrade if the repository is at 2.5?

Cheers

ice.

---

### Post by icedfusion on 2008-01-02
Well, i forced the ownership of nzb to allow access for read/write for everyone - no joy.

I installed python2.4 (didnt uninstall 2.5 as too much depends on it and i am unable to use the 'force version' option) - but in the hellanzb file i forced the version #!/usr/bin/python2.4

Unfortunately, the result is the same - hellanzb fires up but just sits there and doesnt start a download.
:(


Cheers

ice.

---

### Post by icedfusion on 2008-01-14
Seriously, is no one else having this issue?

Of the other packages relating to hellanzb I am using the following versions:

par2cmdline version 0.4,
Python 2.5.1
python-support 0.6.4
python-twisted-core 2.5.0-2build1
python-twisted-web 0.7.0-1
unrar 1:3.7.3-1.1

As far as I am aware, these are all the required packages for hellanzb to run.

If others have the same versions then there must be something else that is preventing hellanzb from actually downloading (yes, my conf file is correct).

Cheers

ice.

---

### Post by Mithrilhall on 2008-01-14
Any firewalls running?


These are the versions I'm running:
```

ms:~$ apt-show-versions
par2/gutsy uptodate 0.4-9
python/gutsy uptodate 2.5.1-1ubuntu2
python-support/gutsy uptodate 0.6.4ubuntu1
python-twisted-core/gutsy uptodate 2.5.0-2build1
python-twisted-web/gutsy uptodate 0.7.0-1
unrar-free/gutsy uptodate 1:0.0.1+cvs20070515-1
unrar/gutsy uptodate 1:3.7.3-1.1

```

I don't have par2cmdline installed

---

### Post by testcees on 2008-01-16
> **icedfusion said:**
> Seriously, is no one else having this issue?


Same  twisted.internet.tcp.Connector will retry in x seconds message here in the debug log and no download:(
Hellanzb did download before.

Solved:
Closing other news-clients!

---

### Post by icedfusion on 2008-01-17
I have absolutely nothing else running. 
To test, i reinstalled Ubuntu (and upadtes) + some packages via automatrix then installed hellanzb.

I will retry without installing automatrix (i did this for the par2 stuff).

I am not even going to update on my main user machine in case an update causes problems on that machine as well.

Cheers

ice.

---

### Post by icedfusion on 2008-01-17
Well, I am back in business!!

I unplugged all my routers (i have many) and connected my 'dodgy' machine straight to my cable modem (reset it for the MAC address to renew) and what do you know...it worked. All things started to download.

Plugged all my routers back in and checked again, everything is lovely.

Cheers for those who took the time to reply.

ice.
:guitar:

---

### Post by mosegris on 2008-01-28
I have exactly the same problem as you described. If my laptop is running wireless it will stop downloading after around 30 sec. If I instead plug it in using cable, I have no problems at all. I can't find a solution to fix this, but it seems to be Twisted that causes the problems...

/mosegris

---

### Post by sheka on 2008-02-13
I have this same issue - I downloaded the hellanzb tar ball from the hellanzb site, configured the conf file and ran the python script - python hellanzb.py -c config file -D 

Everything worked fine

Yet when I ran the Ubuntu supplied version with hellanzb -D I receive all the error messages.  What I have eventually done is created a hellanzb.config.local file in ETC and copied the working config file into there.  I now run hellanzb -c /etc/hellanzb.conf.local -D - Everything works!!

At some point I will check the config files to see why one works and the other causes errors

---

