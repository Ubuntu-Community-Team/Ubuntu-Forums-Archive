---
title: "groupware advice"
date: 2006-10-22
forum: General Help
---

### Post by harty83 on 2006-10-22
Hello all,

I know that there is a lot of documentation about linux groupware out there, but to be honest none of it is worth crap.  Almost every groupware I've looked at, their documentation sucks.

So, I'm turning to the community for experienced advice.

I'm looking for an open source (aka free) Groupware server that must have the following:

1) Email (I already have a courier imap server set up; it just needs to have an email web client)
2) Calendaring
3) Contacts
4) Pocket pc support (syncml)
5) PIM must be able to sync with Evolution and Outlook (outlook not as important)

A bit of history:
I've looked at a lot of different groupware servers such as open-xchange, egroupware, phpgroupware, groupwise, kolab2, citadel, hula, and a bunch more I can't remember at the moment.  I have used Kolab2 for a while, but it lacks pocket pc and decent evolution support.  

I am currently using eGroupware which has met my needs best thus far but I can't get PIM to work correctly in Evolution (multisync sucks [can't get it to work and it duplicates everything], opensync does not seem to support syncing with an already established syncml server, and syncevolution will not sync and returns errors after the first sync).  Citadel looks promising but I can't figure out if it supports syncml (so I can sync my pocket pc).  Any thoughts on that?

Any thoughts, advice, experience, etc will be much appreciated!

Thanks!
Alan

---

### Post by harty83 on 2006-11-04
Found the perfect solution.  I'm now using scheduleworld (scheduleworld.com).  That takes care of all my needs.  Syncevolution works great with it.  And the best part is that I don't have to mess around with installations, configs, etc.  They pretty much do it all for me!

Alan

---

### Post by niels on 2006-11-18
> **harty83 said:**
> Found the perfect solution.  I'm now using scheduleworld (scheduleworld.com).  That takes care of all my needs.  Syncevolution works great with it.  And the best part is that I don't have to mess around with installations, configs, etc.  They pretty much do it all for me!

Alan

Hi, I would like to know how you installed, configured and use SyncEvolution. I can't find any good howto.

---

### Post by harty83 on 2006-11-18
> **niels said:**
> Hi, I would like to know how you installed, configured and use SyncEvolution. I can't find any good howto.

Sure what version are you using?  Back when i compiled I used 0.4. But now it looks like 0.5 is out.  

It looks like they created some precompiled binaries for 0.5.  I couldn't get those to work.  so download the source instead.

[http://sourceforge.net/project/downloading.php?group_id=146288&use_mirror=easynews&filename=syncevolution-0.5.tar.gz&49083195]("http://sourceforge.net/project/downloading.php?group_id=146288&use_mirror=easynews&filename=syncevolution-0.5.tar.gz&49083195")

Unpack it and cd into the unpacked directory (syncevolution-0.5).

Then do 

```

./configure --prefix=/usr
make

```

Now I use checkinstall to create a deb file because it is easy to uninstall later via synaptic.  If you have checkinstall installed you can then do

```
sudo checkinstall
```

Or if you do not do 

```
sudo make install
```

There are a number of dev packages you need to install but I can't remember what they are.  I believe they were libcurl3-dev, evolution-data-server-dev and libdb3-dev.  If you get errors during the ./configure stage, see what it is saying is missing.  Then open synaptic and look for that package (sometimes ubuntu lists the packaged as lib*whatever*).  Install the *whatever*-dev package and reconfigure.  If you have trouble finding something let me know.

As far as configuring syncevolution, you need to create the following directory structure renaming what's iin italics: /home/*your_home*/.sync4j/evolution/*whatever*/spds

Then in the spds directory, create two more directories.  One named "sources" and the other "syncml."

In the sources directory create three more directories: "addressbook," "calendar," and "todo."  

Now for the config files.  In each of those three directories you need a config.txt file.

Here are mine:

addressbook/config.txt
```
# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = addressbook

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = two-way,slow,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/vcard


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = card3

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```

Couple notes: the evolutionsource should be the name of your calendar, addressbook or todo in evolution.  If you have a username and password for evolution, then you need to add them under authentication for Evolution source.  Otherwise leave the username and password blank as I have.  

Here are the other two:

calendar/config.txt
```
# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = calendar

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/calendar


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = cal2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```

todo/config.txt
```
# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = todo

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/x-todo


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = task2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```

Finally, you need to create a config.txt in the /home/*your_home*/.sync4j/evolution/*whatever*/spds/syncml directory.  

Here is mine:

```
# the base URL of the SyncML server:
# - Sync4j 2.3
#syncURL = http://hartys.org:1972/egroupware/rpc.php
# - Funambol >= 3.0
#syncURL = http://localhost:8080/funambol/ds
# - sync.scheduleworld.com
syncURL = http://sync.scheduleworld.com/funambol/ds

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = sc-api-nat-hartysdesktop

# authorization for the SyncML server
username = 
password = 

# set to T to enable an HTTP proxy
useProxy = 0
# proxy URL (http://<host>:<port>)
proxyHost = 
# user agent string used for HTTP
userAgent = SyncEvolution

# full path to directory where automatic backups and logs
# are stored for all synchronizations; if empty, the temporary
# directory "$TMPDIR/SyncEvolution-<username>-<server>" will
# be used to keep the data of just the latest synchronization run
logdir =

# Unless this option is set, SyncEvolution will never delete
# anything in the "logdir". If set, the oldest directories and
# all their content will be removed after a successful sync
# to prevent the number of log directories from growing beyond
# the given limit.
maxlogdirs =

# This value is the number of changes which are sent to the
# server at once. It is set to a very large number to work around
# problems in either client library or server when items are
# actually sent in multiple chunks during a slow sync - do not edit!
maxModPerMsg = 100000

# used by the SyncML library internally; do not modify
begin =0
end =0
firstTimeSyncMode = 0

serverID = 
serverPWD = 
serverNonce = 
clientNonce = 
clientAuthType = 
serverAuthType = 
isServerAuthRequired = 0
proxyPort = 0
proxyUsername = 
proxyPassword = 
checkConn = 0
responseTimeout = 0
readBufferSize = 0
maxMsgSize = 0
encryption = 0

```

Fill in the username and password with what is given to you by scheduleworld.  Customize the device name.

Now to run, do 
```
syncevolution *whatever*
```

with the whatever being what you named /home/*your_home*/.sync4j/evolution/*whatever*

That should do it.  Let me know if you have any problems.

Alan

---

### Post by niels on 2006-11-18
Thank you for the quick answer...

> **harty83 said:**
> Sure what version are you using?  Back when i compiled I used 0.4. But now it looks like 0.5 is out.  

It looks like they created some precompiled binaries for 0.5.  I couldn't get those to work.  so download the source instead.

[http://sourceforge.net/project/downloading.php?group_id=146288&use_mirror=easynews&filename=syncevolution-0.5.tar.gz&49083195]("http://sourceforge.net/project/downloading.php?group_id=146288&use_mirror=easynews&filename=syncevolution-0.5.tar.gz&49083195")

Unpack it and cd into the unpacked directory (syncevolution-0.5).

Then do 

```

./configure --prefix=/usr
make

```


I got this far, but the ./configure resulted in the following:
```
niels@niels-laptop:~/Download/syncevolution-0.5$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
configure: configuring the client library 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
configure: error: configuring client library failed 
niels@niels-laptop:~/Download/syncevolution-0.5$
```

Do you know what the problem is?

I have attached the log-file.

---

### Post by harty83 on 2006-11-18
Looks like you don't have a compiler installed.

Try this and then reconfigure:

```
sudo apt-get install build-essential
```

---

### Post by niels on 2006-11-18
> **harty83 said:**
> Looks like you don't have a compiler installed.

Try this and then reconfigure:

```
sudo apt-get install build-essential
```

Ok. I figured it out and installed the g++ and evolution-data-dev.

After following your other instructions, everything seems to work! Tank you!

---

### Post by MarkSwanson on 2006-11-23
harty83 - that was a very helpful post. You rock.

---

### Post by jackyyll on 2006-11-24
When i try to configure i get this error:

```
checking for libcurl... missing
configure: error: libcurl is required, check that its development package is installed and curl-config is in your PATH
configure: error: configuring client library failed 

```

How do i get libcurl?

---

### Post by harty83 on 2006-11-24
> **jackyyll said:**
> When i try to configure i get this error:

```
checking for libcurl... missing
configure: error: libcurl is required, check that its development package is installed and curl-config is in your PATH
configure: error: configuring client library failed 

```

How do i get libcurl?

```
sudo apt-get install libcurl3 libcurl3-dev
```

---

### Post by jackyyll on 2006-11-24
Thanks that worked :) But.. Now i'm getting a new error :(

```
checking for EPACKAGE... checking for EPACKAGE... checking for EPACKAGE... configure: error: No compatible evolution-data-server was found.

Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libecal, libedata, evolution-data-server
and libedataserver.

You can check that these packages are available by running
pkg-config --list-all.

```

Help please? :)

---

### Post by harty83 on 2006-11-25
> **jackyyll said:**
> Thanks that worked :) But.. Now i'm getting a new error :(

```
checking for EPACKAGE... checking for EPACKAGE... checking for EPACKAGE... configure: error: No compatible evolution-data-server was found.

Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libecal, libedata, evolution-data-server
and libedataserver.

You can check that these packages are available by running
pkg-config --list-all.

```

Help please? :)

```
sudo apt-get install evolution-data-server-dev
```

---

### Post by hrabeX on 2006-11-29
I've installed syncevolution and made all the configuraton, but i gives me some errors:

**addressbook sync only:**
segmentation fault

**to-do sync only**:
17:00:26 GMT +1:00 [ERROR] - todo: parsing ical<task><Body></Body><DateCompleted>0</DateCompleted><DueDate>0</DueDate><Importance>1</Importance><PercentComplete>0</PercentComplete><Sensitivity>0</Sensitivity><StartDate>0</StartDate><Status>1</Status><Subject>kontaktovat Pavla Kope&#269;ka ohledn&#283; Anselmiady (benediktini)</Subject><ActualWork>0</ActualWork><IsRecurring>0</IsRecurring>: failed.
17:00:26 GMT +1:00 [DEBUG] - libcurl info: Connection #0 to host m2ai.com left intact
17:00:26 GMT +1:00 [DEBUG] - <SyncML><SyncHdr><VerDTD>1.1</VerDTD><VerProto>SyncML/1.1</VerProto><SessionID>1164816023</SessionID><MsgID>5</MsgID><Target><LocURI>rat-look</LocURI></Target><Source><LocURI>http://m2ai.com/egroupware/rpc.php</LocURI></Source><RespURI>http://m2ai.com/egroupware/rpc.php?syncml_sessionid=syncml-28f235259218799cf6c4259b612b8366</RespURI></SyncHdr><SyncBody><Status><CmdID>1</CmdID><MsgRef>5</MsgRef><CmdRef>0</CmdRef><Cmd>SyncHdr</Cmd><TargetRef>http://m2ai.com/egroupware/rpc.php</TargetRef><SourceRef>rat-look</SourceRef><Data>212</Data></Status><Final></Final></SyncBody></SyncML>
17:00:26 GMT +1:00 [DEBUG] - Response read
17:00:26 GMT +1:00 [DEBUG] - Committing source todo (next: 1164816024)
17:00:26 GMT +1:00 [DEBUG] - ret: 0, lastErrorCode: 1, lastErrorMessage: todo: parsing ical<task><Body></Body><DateCompleted>0</DateCompleted><DueDate>0</DueDate><Importance>1</Importance><PercentComplete>0</PercentComplete><Sensitivity>0</Sensitivity><StartDate>0</StartDate><Status>1</Status><Subject>kontaktovat xxxxx (xxxxx)</Subject><ActualWork>0</ActualWork><IsRecurring>0</IsRecurring>: failed

[SIZE="1"][I]17:00:26 GMT +1:00 [ERROR] - Error in ending sync: todo: parsing ical<task><Body></Body><DateCompleted>0</DateCompleted><DueDate>0</DueDate><Importance>1</Importance><PercentComplete>0</PercentComplete><Sensitivity>0</Sensitivity><StartDate>0</StartDate><Status>1</Status><Subject>kontaktovat xxxxx (xxxxx)</Subject><ActualWork>0</ActualWork><IsRecurring>0</IsRecurring>: failed
17:00:26 GMT +1:00 [DEBUG] - libcurl info: Closing connection #0[/I][/SIZE]



**calendar sync only:**
17:19:36 GMT +1:00 [ERROR] - calendar: parsing ical<appointment><Start>2005-06-29</Start><End>2005-06-29</End><AllDayEvent>1</AllDayEvent><Body></Body><Categories></Categories><Importance>1</Importance><Location></Location><ReminderSet>0</ReminderSet><Sensitivity>0</Sensitivity><Subject>xxxxxxx</Subject></appointment>: failed

[SIZE="1"][I]17:19:35 GMT +1:00 [DEBUG] - <SyncML><SyncHdr><VerDTD>1.1</VerDTD><VerProto>SyncML/1.1</VerProto><SessionID>1164817171</SessionID><MsgID>5</MsgID><Target><LocURI>rat-look,</LocURI></Target><Source><LocURI>http://m2ai.com/egroupware/rpc.php</LocURI></Source><RespURI>http://m2ai.com/egroupware/rpc.php?syncml_sessionid=syncml-5d46b39e3900dff0606acddd8924f5cd</RespURI></SyncHdr><SyncBody><Status><CmdID>1</CmdID><MsgRef>5</MsgRef><CmdRef>0</CmdRef><Cmd>SyncHdr</Cmd><TargetRef>http://m2ai.com/egroupware/rpc.php</TargetRef><SourceRef>rat-look,</SourceRef><Data>212</Data></Status><Final></Final></SyncBody></SyncML>
17:19:35 GMT +1:00 [DEBUG] - Response read
17:19:35 GMT +1:00 [DEBUG] - Committing source calendar (next: 1164817172)
17:19:35 GMT +1:00 [DEBUG] - ret: 0, lastErrorCode: 1, lastErrorMessage: calendar: parsing ical<appointment><Start>2005-06-29</Start><End>2005-06-29</End><AllDayEvent>1</AllDayEvent><Body></Body><Categories></Categories><Importance>1</Importance><Location></Location><ReminderSet>0</ReminderSet><Sensitivity>0</Sensitivity><Subject>Výro&#269;í u&#382;ivatele Pavel</Subject></appointment>: failed
17:19:35 GMT +1:00 [ERROR] - Error in ending sync: calendar: parsing ical<appointment><Start>2005-06-29</Start><End>2005-06-29</End><AllDayEvent>1</AllDayEvent><Body></Body><Categories></Categories><Importance>1</Importance><Location></Location><ReminderSet>0</ReminderSet><Sensitivity>0</Sensitivity><Subject>Výro&#269;í u&#382;ivatele Pavel</Subject></appointment>: failed
17:19:35 GMT +1:00 [DEBUG] - libcurl info: Closing connection #0[/I][/SIZE]


any suggestions, please?

---

### Post by harty83 on 2006-11-29
What server are you trying to sync with?  scheduleworld? egroupware? etc?

---

### Post by ziegs on 2006-11-30
hey i'm getting an error when I try to sync:

03:31:32 GMT -5:00 [INFO] - Synchronization URL: [http://sync.scheduleworld.com/funambol/ds](http://sync.scheduleworld.com/funambol/ds)
03:31:32 GMT -5:00 [INFO] - Preparing synchronization of calendar_1...
03:31:33 GMT -5:00 [ERROR] - Client not authenticated
03:31:33 GMT -5:00 [ERROR] - Error in preparing sync:

My username and password are _definitely_ right.  ideas?

---

### Post by hrabeX on 2006-11-30
> **harty83 said:**
> What server are you trying to sync with?  scheduleworld? egroupware? etc?
egroupware

Finall, I've got it worked, (the name of server's database is calendar instead ./calendar in egw docs) but SyncEvolution erased all recurring entries in egw calendar:(

---

### Post by hrabeX on 2006-12-04
The another problem:
Inputs in Evolution doesn't appears in eGroupware, and items synced from egw have problem with character coding :(
e.g:
Zdraví - objednat se k zuba&#345;ce-----zdrav=C3=AD - objednat se k zuba=C5=99ce

please could you be so kind and post me your syncevolution egw settings?
 Thanks.

---

### Post by sander2 on 2006-12-15
> **ziegs said:**
> hey i'm getting an error when I try to sync:

03:31:32 GMT -5:00 [INFO] - Synchronization URL: [http://sync.scheduleworld.com/funambol/ds](http://sync.scheduleworld.com/funambol/ds)
03:31:32 GMT -5:00 [INFO] - Preparing synchronization of calendar_1...
03:31:33 GMT -5:00 [ERROR] - Client not authenticated
03:31:33 GMT -5:00 [ERROR] - Error in preparing sync:

My username and password are _definitely_ right.  ideas?

Hi!

I get the same error, and my username/password is right too. did you get it working?

---

### Post by harty83 on 2006-12-16
Don't know if this is right but maybe a thought: Login to your scheduleworld account and click on preferences.  Find the client you are trying to sync and see if there is anything you need to "approve."  I can't remember if I had to do that or not when I first tried to sync my client.

---

### Post by gaebriel on 2006-12-16
Have you tried the horde project [http://horde.org]("http://horde.org")? I started working with the Groupware Webmail Edition [http://www.horde.org/webmail/]("http://www.horde.org/webmail/") a couple weeks ago and it seems pretty good so far. I haven't tried the syncing yet, but I remember there is a module for that included.

---

### Post by shrift on 2006-12-21
First, Thank you for the little how to Harty83, that was useful.

I set my directories like this: ```
bmartens@ender:~/.sync4/evolution/one/spds/sources/
```
So I followed your directions, seems like I got it all right, but when I run "syncevolution one" it tells me 

```
bmartens@ender:~$ syncevolution one
12:44:53 GMT -6:00 [ERROR] - no syncURL configured - perhaps the server name "one" is wrong?
12:44:53 GMT -6:00 [ERROR] - cannot proceed without configuration
bmartens@ender:~$ 

```


Any ideas?

---

### Post by harty83 on 2006-12-21
> **shrift said:**
> First, Thank you for the little how to Harty83, that was useful.

I set my directories like this: ```
bmartens@ender:~/.sync4/evolution/one/spds/sources/
```
So I followed your directions, seems like I got it all right, but when I run "syncevolution one" it tells me 

```
bmartens@ender:~$ syncevolution one
12:44:53 GMT -6:00 [ERROR] - no syncURL configured - perhaps the server name "one" is wrong?
12:44:53 GMT -6:00 [ERROR] - cannot proceed without configuration
bmartens@ender:~$ 

```


Any ideas?

First of all is did you accidentally leave off the "j" in > ~/.sync4/evolution/one/spds/sources/?  It is suppose to be "~/.sync4j" 

Do you have the directory ~/.sync4j/evolution/one/spds/syncml/?

If not, then you need to have that directory along with a config.txt in it.  Mine is like the following:

```
# the base URL of the SyncML server:
# - Sync4j 2.3
#syncURL = http://hartys.org:1972/egroupware/rpc.php
# - Funambol >= 3.0
#syncURL = http://localhost:8080/funambol/ds
# - sync.scheduleworld.com
syncURL = http://sync.scheduleworld.com/funambol/ds

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = sc-api-nat-hartysdesktop

# authorization for the SyncML server
username = 
password = 

# set to T to enable an HTTP proxy
useProxy = 0
# proxy URL (http://<host>:<port>)
proxyHost = 
# user agent string used for HTTP
userAgent = SyncEvolution

# full path to directory where automatic backups and logs
# are stored for all synchronizations; if empty, the temporary
# directory "$TMPDIR/SyncEvolution-<username>-<server>" will
# be used to keep the data of just the latest synchronization run
logdir =

# Unless this option is set, SyncEvolution will never delete
# anything in the "logdir". If set, the oldest directories and
# all their content will be removed after a successful sync
# to prevent the number of log directories from growing beyond
# the given limit.
maxlogdirs =

# This value is the number of changes which are sent to the
# server at once. It is set to a very large number to work around
# problems in either client library or server when items are
# actually sent in multiple chunks during a slow sync - do not edit!
maxModPerMsg = 100000

# used by the SyncML library internally; do not modify
begin =0
end =0
firstTimeSyncMode = 0

serverID = 
serverPWD = 
serverNonce = 
clientNonce = 
clientAuthType = 
serverAuthType = 
isServerAuthRequired = 0
proxyPort = 0
proxyUsername = 
proxyPassword = 
checkConn = 0
responseTimeout = 0
readBufferSize = 0
maxMsgSize = 0
encryption = 0
```

Add your username and password.

---

### Post by gardara on 2007-01-02
awesome tutorial harty83.

I was thinking about switching over to thunderbird because I found syncing with evolution confusing.

Thanks a lot :)

---

### Post by elektronaut on 2007-01-05
Just a little remark for those people who are getting authentication failures: 
1) You have to use the identification number on the preferences page as username, not your email address or the login name for the scheduleworld website.
2) Keep an eye on whitespaces AFTER your username or password. I had one after my username, it took me some time to find out that this was the cause for the error...

---

### Post by vanlue on 2007-01-07
> **harty83 said:**
> 
Unpack it and cd into the unpacked directory (syncevolution-0.5).

Then do 

```

./configure --prefix=/usr
make

```


First: thanks, harty, for the great how-to and for graciously helping others out.

I'm having an issue, however, and was hoping you or someone might have a good idea.

After I run:
```

./configure --prefix=/usr

```
everything runs nicely until it gets to this point and it gives me an error:
```

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EPACKAGE... checking for EPACKAGE... checking for EPACKAGE... configure: error: No compatible evolution-data-server was found.

Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libecal, libedata, evolution-data-server
and libedataserver.

You can check that these packages are available by running
pkg-config --list-all.

```

From what I can tell I have libecal, libedata, evolution-data-server and libedataserver installed.  The output of *pkg-config --list-all* is in list.txt, attached to this post.

Thanks in advance for the help!

---

### Post by harty83 on 2007-01-07
> **vanlue said:**
> First: thanks, harty, for the great how-to and for graciously helping others out.

I'm having an issue, however, and was hoping you or someone might have a good idea.

After I run:
```

./configure --prefix=/usr

```
everything runs nicely until it gets to this point and it gives me an error:
```

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EPACKAGE... checking for EPACKAGE... checking for EPACKAGE... configure: error: No compatible evolution-data-server was found.

Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libecal, libedata, evolution-data-server
and libedataserver.

You can check that these packages are available by running
pkg-config --list-all.

```

From what I can tell I have libecal, libedata, evolution-data-server and libedataserver installed.  The output of *pkg-config --list-all* is in list.txt, attached to this post.

Thanks in advance for the help!

make sure you have evolution-data-server-dev installed.

---

### Post by vanlue on 2007-01-07
Excellent!!!

Looking at the issue now, it probably seems like a dumb question to have asked, especially since you already explained that evolution-data-server-dev needed to be installed.

It works perfectly now.

Your help & patience is much appreciated!

---

### Post by vegaskarma on 2007-01-08
After reading this post I was able to set up syncevolution and am very happy with the results. Now I just need one more thing to make it complete, automate the syncing process. Can anyone help me with that, maybe gnome-schedule could do this but I couldn't figure it out.

---

### Post by suamme1 on 2007-01-18
> **vegaskarma said:**
> After reading this post I was able to set up syncevolution and am very happy with the results. Now I just need one more thing to make it complete, automate the syncing process. Can anyone help me with that, maybe gnome-schedule could do this but I couldn't figure it out.

It's not completely automated, but I simply created a button for my top panel and put the Evolution icon on it. Now anytime I want to sync, just click the button and wait a bit. It works great for me since it's my notebook and I don't use it nearly as often as my desktop.

---

### Post by Cocooningweb on 2007-01-20
I get the following error:
> fhoude@Francois:~$ syncevolution blackberry
11:53:07 GMT -5:00 [ERROR] - no syncURL configured - perhaps the server name "blackberry" is wrong?
11:53:07 GMT -5:00 [ERROR] - cannot proceed without configuration


I created three config.txt files using the tutorial at the beginning of this thread:
/home/fhoude/.sync4j/evolution/blackberry/spds/sources/addressbook
/home/fhoude/.sync4j/evolution/blackberry/spds/sources/calendar
/home/fhoude/.sync4j/evolution/blackberry/spds/sources/todo

I  also created a config.txt file in the following directory and added my ScheduleWorld user and password in the "# authorization for the SyncML server" section of the file.
/home/fhoude/.sync4j/evolution/blackberry/spds/syncml

Any idea anyone? Thanks

---

### Post by Cocooningweb on 2007-01-25
OK got it.. I'm one step closer. I created my config files with Kate and they didn't have the .txt extension. I renamed them but now I'm stuck with another error.

Here's what I get:
fhoude@Francois:~$ syncevolution scheduleworld
Segmentation fault

Any idea?

---

### Post by laser_in_your_eye on 2007-01-29
I got to the checkinstall step and get the following error message: 

make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

I get the same thing with make install.  Anyone know where I am going wrong?


Okay fixed that problem--just needed to cd into the correct folder.  Nevermind!

---

### Post by liorhakim on 2007-01-29
when i try to do ./configure --prefix=/usr make
i get the following :

```

configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
configure: configuring the client library 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for libcurl... found
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating include/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
checking for make-pkg-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EPACKAGE... checking for EPACKAGE... checking for EPACKAGE... configure: error: No compatible evolution-data-server was found.

Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libecal, libedata, evolution-data-server
and libedataserver.

You can check that these packages are available by running
pkg-config --list-all.


```

and the pkg-config --list-all out put is

```
deskbar-applet          Deskbar Applet Handlers Location - Providing the location of deskbar-applet system-wide handlers.
gnome-system-tools      gst - Gnome System Tools
gdict-1.0               gdict-1.0 - GNOME Dictionary Protocol client library
libidn                  Libidn - IETF stringprep, nameprep, punycode, IDNA text processing.
openssl                 OpenSSL - Secure Sockets Layer and cryptography libraries and tools
gnome-mime-data-2.0     gnome-mime-data - Base set of file types and applications for GNOME
gtkhtml-sharp-2.0       Gtkhtml - Gtkhtml
mono-cairo              Mono.Cairo - Cairo bindings for Mono
glade-sharp-2.0         Glade - Glade
gconf-sharp-2.0         GConf - GConf
libssl                  OpenSSL - Secure Sockets Layer and cryptography libraries
gst-python-0.10         gst-python - Python bindings for GStreamer
gnome-vfs-sharp-2.0     GnomeVfs - GnomeVfs
gnome-doc-utils         gnome-doc-utils - GNOME Documentation Utilities
libcrypto               OpenSSL-libcrypto - OpenSSL cryptography library
rsvg-sharp-2.0          Rsvg - Rsvg
xml2po                  xml2po - Tool for translating XML documents
fontutil                FontUtil - Font utilities dirs
tomboy-plugins          Tomboy Plugin Library - Library providing the interfaces for Tomboy plugins
glib-sharp-2.0          GLib - GLib
iso-codes               iso-codes - ISO country, language and currency codes and translations
gnome-sharp-2.0         Gnome - Gnome
com_err                 com_err - Common error description library
beryl-settings-bindings beryl-settings-bindings - Beryl settings bindings
xbitmaps                X bitmaps - Bitmaps that are shared between X applications
libcurl                 libcurl - Library to transfer files with ftp, http, etc.
gnome-screensaver       gnome-screensaver - gnome screensaver
gtk-dotnet-2.0          Gtk.DotNet - .NET Extensions for Gtk
shared-mime-info        shared-mime-info - Freedesktop common MIME database
art-sharp-2.0           Art - Art
gtk-sharp-2.0           Gtk - Gtk
gmime-sharp             gmime-sharp - .NET binding for GMime
gnome-icon-theme        gnome-icon-theme - A collection of icons used as the basis for GNOME themes
dbus-sharp              DBus - DBus

```

and sudo apt-get install evolution-data-server

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution-data-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

what should i do?


> **harty83 said:**
> 

Then do 

```

./configure --prefix=/usr
make

```



---

### Post by laser_in_your_eye on 2007-01-30
I have everything configured, but the sync time is INCREDIBLY long.  Any ideas on how to speed things up?

---

### Post by jvaudrey on 2007-01-31
Hello

I managed to get this working without any problems thank you for a great walkthrough.

The one problem i do have is that when i sync with schedulewold all the calendar items are marked personal so are not synced with google, i have to change each one of them manually.

Do you know what i am doing wrong?

Thanks

John

---

### Post by mrwooster on 2007-02-02
Works a treat

I now feel very sophisticated: my phone <-> evolution <-> scheduleworld <-> google

What a geek ;-)

---

### Post by claypole on 2007-02-05
Thanks for this.  I now have my home Ubuntu PC, work Win/Outlook laptop, work Exchange Server, P990i mobile and Google Calendar all synced!! :guitar:

I am using syncevolution, ScheduleWorld and Dataviz ActiveSync client on my P990i

Also, I couldn't get the local Funambol server to sync with evolution using syncevolution (and there are some restrictions even if you can), and there are some really nice features in ScheduleWorld.

---

### Post by xand on 2007-02-13
I got stuck on the same thing as CocooningWeb...tried to find anything related but there's not much about it.
```

xand@xand-desktop:~$ syncevolution whatever
Falha de segmentação (core dumped)

```

Does anything has to be configured in ScheduleWorld Preferences? I used to sync with Outlook before, i wonder if something must change there...

Runnin Ubuntu 6.10, syncevolution 0.5.

---

### Post by Sariel Amraphel on 2007-02-16
seems it doesn't want to work for me.....

> 
 syncevolution pub
12:07:40 GMT +1:00 [ERROR] - Error in sync() - configuration not set correctly.

Synchronization failed, see /tmp/SyncEvolution-jf-pub for details.

Modifications:

12:07:40 GMT +1:00 [ERROR] - sync failed without an error description, check log


syncml/config.txt:
> 
syncURL = [http://hostname:8000/egroupware/rpc.php](http://hostname:8000/egroupware/rpc.php)

deviceId = sc-api-nat-evolution

username = xxxxxxxxxxxx
password = xxxxxxxxxxxx

useProxy = 0
proxyHost = 
userAgent = SyncEvolution

logdir =

maxlogdirs =

maxModPerMsg = 100000

begin =0
end =0
firstTimeSyncMode = 0

serverID = xxxxxxx
serverPWD = xxxxxxxxxxxxx
serverNonce = 
clientNonce = 
clientAuthType = 
serverAuthType = 
isServerAuthRequired = 0
proxyPort = 0
proxyUsername = 
proxyPassword = 
checkConn = 0
responseTimeout = 0
readBufferSize = 0
maxMsgSize = 0
encryption = 0



calendar/config.txt
> 
name = calendar

sync = two-way

syncModes = slow,two-way,refresh-from-client,refresh-from-server

type = text/calendar

evolutionsource = Personal

uri = ./calendar

evolutionuser =
evolutionpassword = 

last = 0


The server's configured to require a password to access the rpc.php using basic authentication besides the normal username/password for the calendaring.

What'd I do wrong?

---

### Post by thierrybo on 2007-02-25
Marvelous, it works perfectly with my old Breezy. I can now sync Evolution <-> ScheduleWorld/Google Calendar, then my also old nokia 7650 <->  ScheduleWorld/Google Calendar then Palm <-> Evolution, all in sync. I had a few duplicates first but know it works fine.

---

### Post by r_mano on 2007-03-08
Hi...

a couple of thing (well, three:)
[LIST]
[*]maybe a chmod o-r .sync4j/.../syncml/config.txt (which contains the password in plain) would be sensible...
[*]I have tried to synchronize the calendar with my Nokia9500. The thing went quite well, but the recurring event lost all the exception (I mean: I normally set up a recurring event over a period and then "modify just this ocurrence" for the affected items.) All of this was lost in the synchornization from nokia 9500 to scheduleworld
[*] and now the worst: the repeated event that cross DST change time has the occurrences after the DST change saved with an hour difference. I tried with or without "ignore DST" in scheduleworld configuratiom.
[/LIST]

¿Has anyone some suggestion here? I tried the ScheduleWorld formu, but it seems they're busted, they do not send me the confirmation email (after saying so).

Anyway, thank you for the help. But I feel that the time I can have my two PCs (work and home) easily synchronized in linux is quite far away. Not speaking of the portable phone...

---

### Post by maddentim on 2007-03-12
hello,
thanks for the guide. having trouble with getting it to go...

getting this error:

tim@tim-desktop:~$ syncevolution /home/tim/.sync4j/one
09:49:39 GMT -6:00 [ERROR] - no syncURL configured - perhaps the server name "/home/tim/.sync4j/one" is wrong?
09:49:39 GMT -6:00 [ERROR] - cannot proceed without configuration

I am using the config.txt files that are recommeded with my username/password inserted.  Pretty sure i have the directories set up.  Thanks for any help.

Tim

---

### Post by maddentim on 2007-03-14
> **maddentim said:**
> hello,
thanks for the guide. having trouble with getting it to go...

getting this error:

tim@tim-desktop:~$ syncevolution /home/tim/.sync4j/one
09:49:39 GMT -6:00 [ERROR] - no syncURL configured - perhaps the server name "/home/tim/.sync4j/one" is wrong?
09:49:39 GMT -6:00 [ERROR] - cannot proceed without configuration

I am using the config.txt files that are recommeded with my username/password inserted.  Pretty sure i have the directories set up.  Thanks for any help.

Tim
I email the scheduleworld support and they said it was a bug that was in there for a day.  Works now for calendar.  Is it suppose to sync my contacts to with Google? It isn't...

---

### Post by minithommo on 2007-03-14
Hi Guys,

I am trying to use ScheduleWorld combined with SyncEvolution, Evolution and my Nokia E61.

I have followed these instructions, they are very easy to understand and follow thank you.

I am getting the following error, if anyone knows how to fix it, greatly appreciated:

When I run 'syncevolution'

> 00:24:50 GMT +10:00 [ERROR] - : type '' empty or unknown

** (process:19803): WARNING **: FIXME: wait for completion unimplemented


If I run it with administrator rights:

> thommo@thommo-laptop:~/.evolution/addressbook/local/system$ sudo syncevolution sync
00:24:48 GMT +10:00 [ERROR] - addressbook: no such address book: 'file:///home/thommo/.evolution/addressbook/local/system'


Even though I that directory exists and there are an addressbook.db and addressbook.db.summary there.

The reason it is listing that file as the address book rather than 'Personal' is because I had Personal initially but it did not work, so I specified the file URI that I found by running just 'syncevolution'.

Any ideas?  I am kinda new to this stuff so any help would be appreciated.

Thanks,

Thommo

---

### Post by tareko on 2007-03-15
Hello all!

Harty83 provided an excellent howto, but it is a little difficult to follow mindlessly. Extra info also from [Amedee's site]("http://amedee.be/?q=node/4"). Here is a version I think is easier to follow:

*Note*: Tested with Feisty and syncevolution 0.5

**INSTALLATION**
1. Install needed libraries and tools:
```
sudo apt-get install build-essential checkinstall evolution evolution-dev evolution-data-server evolution-data-server-dev libcurl3-dev libedataserver1.2-dev libebook1.2-dev libecal1.2-dev libedata-book1.2-dev libedata-cal1.2-dev libedataserverui1.2-dev gconf2 gconf2-common libgconf2-4 libgconf11 libgconf2-dev libgconf-dev
```

2. Download and unzip SyncEvolution, then go into the directory.
```
wget "http://easynews.dl.sourceforge.net/sourceforge/sync4jevolution/syncevolution-0.5.tar.gz"
tar -xvf syncevolution-0.5.tar.gz
cd syncevolution-0.5
```

3. Issue configure command.
```
./configure --prefix=/usr
```

4. Compile the program
```
make
```

5. Make a Debian package that can be used to easily manipulate the package. Fill out the information as desired.
```
sudo checkinstall
```

6. Install the package.
```
sudo dpkg -i syncevolution*.deb
```


**CONFIGURATION**

7. Make necessary directories. (Note: You can replace "sync1" with your own string, or leave as is)
```
mkdir ~/.sync4j
mkdir ~/.sync4j/evolution
mkdir ~/.sync4j/evolution/sync1
mkdir ~/.sync4j/evolution/sync1/spds
mkdir ~/.sync4j/evolution/sync1/spds/syncml
mkdir ~/.sync4j/evolution/sync1/spds/sources
mkdir ~/.sync4j/evolution/sync1/spds/sources/addressbook
mkdir ~/.sync4j/evolution/sync1/spds/sources/calendar
mkdir ~/.sync4j/evolution/sync1/spds/sources/todo

```

8. Configuration files (config.txt) will be needed for each of addressbook, calendar, and todo, as well as the syncml file.

```
gedit ~/.sync4j/evolution/sync1/spds/sources/addressbook/config.txt
```
Below is Harty83's configuration. Note that *evolutionsource* should be the name of your calendar, address book or task list in Evolution. If you have a username and password for evolution, then you need to add them under authentication for Evolution source. Otherwise leave the username and password blank as below.

```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = addressbook

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = two-way,slow,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/vcard


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = card3

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```

```
gedit ~/.sync4j/evolution/sync1/spds/sources/calendar/config.txt
```

Harty83's configuration:
```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = calendar

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/calendar


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = cal2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```


```
gedit ~/.sync4j/evolution/sync1/spds/sources/todo/config.txt
```
Harty83's configuration:
```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = todo

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/x-todo


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = task2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```


```
gedit ~/.sync4j/evolution/sync1/spds/syncml/config.txt
```

Fill in the username and password with what is given to you by scheduleworld. You can also customize the device name. Ensure that each device has a unique device name. Harty83's configuration:
```

# the base URL of the SyncML server:
# - Sync4j 2.3
#syncURL = http://hartys.org:1972/egroupware/rpc.php
# - Funambol >= 3.0
#syncURL = http://localhost:8080/funambol/ds
# - sync.scheduleworld.com
syncURL = http://sync.scheduleworld.com/funambol/ds

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = sc-desktop1

# authorization for the SyncML server
username = 
password = 

# set to T to enable an HTTP proxy
useProxy = 0
# proxy URL (http://<host>:<port>)
proxyHost = 
# user agent string used for HTTP
userAgent = SyncEvolution

# full path to directory where automatic backups and logs
# are stored for all synchronizations; if empty, the temporary
# directory "$TMPDIR/SyncEvolution-<username>-<server>" will
# be used to keep the data of just the latest synchronization run
logdir =

# Unless this option is set, SyncEvolution will never delete
# anything in the "logdir". If set, the oldest directories and
# all their content will be removed after a successful sync
# to prevent the number of log directories from growing beyond
# the given limit.
maxlogdirs =

# This value is the number of changes which are sent to the
# server at once. It is set to a very large number to work around
# problems in either client library or server when items are
# actually sent in multiple chunks during a slow sync - do not edit!
maxModPerMsg = 100000

# used by the SyncML library internally; do not modify
begin =0
end =0
firstTimeSyncMode = 0

serverID = 
serverPWD = 
serverNonce = 
clientNonce = 
clientAuthType = 
serverAuthType = 
isServerAuthRequired = 0
proxyPort = 0
proxyUsername = 
proxyPassword = 
checkConn = 0
responseTimeout = 0
readBufferSize = 0
maxMsgSize = 0
encryption = 0

```


**SYNCHRONIZE**
9. You should now be able to synchronize!
```
syncevolution sync1
```

Good luck!

tarek : )

---

### Post by xand on 2007-03-15
These are so awesome tutorials..however that makes me feel even worse since i still can't get it to work..

I just followed the instructions over again and syncevolution still gives me a segmentation fault message when trying to sync to scheduleworld..

I'm running EdgyEft and syncevolution 0.5, and i'm really clueless. Could it be some extra conf that has to be done in ScheduleWorld, since i've already synced with Outlook before? On the General Preferences of SW i have as "SyncML Device" the "sc-pim-outlook ( funambol outlook plug-in 3.0.7 )". Well, if i need to change this, i don't know how to do it as well...

AHHHGGGHHH!

---

### Post by Flak Magnet on 2007-03-23
My thanks to liorhakim for reposting an edited and more cohesive How-To.

I have it working.  One thing I ran into was that I had the syncml directory under "sources"

In the logfile it report one line complaining about an error in "Sync()"

If that sounds familiar to anyone, double/triple check your configuration files AND their directory structure.

I'm now syncing:  Evolution (Personal AND Groupwise) <> Scheduleworld <> Dell Axim X51 (Funambol client)

Yay!

--Flak Magnet

---

### Post by wessel_k on 2007-03-25
Hi,

I used the how-to above to setup syncevolution. And it seems to work. But the only thing I can't get properly configured is the way it syncs calendar items. It only syncs the last month, not even the current one. Any suggestions what I'm missing here?

Regards,

Wessel

---

### Post by quickwitt on 2007-03-28
Help!

I followed the very helpful how-to and everything went well until I tried to sync...

[PHP]syncevolution sync1[/PHP]

I recieved the following error message right away

[PHP][ERROR] - basic_string::_S_construct NULL not valid[/PHP]

I truly have no idea where to go from here.

Thanks in advance.

---

### Post by vav on 2007-04-11
A great tutorial !!  Which means even dumb people like me can now stay in sync.
dumb question:

Do I have to manually do 'syncevolution whatever' every day to sync? Or just run it once and it does its job forever? 

Thanks

---

### Post by tareko on 2007-04-11
Sorry that I can't provide more detail, but do a search for "cron" or "crontab". You can likely easily set something up that way.

tarek : )

---

### Post by vav on 2007-04-11
I have a problem syncing my google contacts in scheduleworld sync.... only 4-5 contacts show up!

I want to sync google contacts with evolution and my smartphone through outlook-scheduleworld, but unless this problem is sorted I'm stuck :(

What could be the problem?

---

### Post by maddentim on 2007-04-11
@vav,

I don't think that Google has set up its contacts to sync with the outside world like they have the calendar.  Syncevolution will get your contacts into scheduleworld (you can check that on the site, there is a little folder (i think) icon next to the calendar icons, it loads a little slow), but I don't think that when you sync from scheduleworld to google, your contact can be sync (today).  Not that it is useless having your contacts on scheduleworld though... you can syncml to many mobile phones these days from motorola, nokia, sonyericson..., plus maybe google is working on it...

---

### Post by maddentim on 2007-04-11
@tareko

Thanks for the crontab tip.  I had been wondering how to set up a periodic sync.  Never had the time to look into it.  It was a piece of cake!

---

### Post by almagas on 2007-04-25
> **tareko said:**
> Hello all!

Harty83 provided an excellent howto, but it is a little difficult to follow mindlessly. Extra info also from [Amedee's site]("http://amedee.be/?q=node/4"). Here is a version I think is easier to follow:

*Note*: Tested with Feisty and syncevolution 0.5

**INSTALLATION**
1. Install needed libraries and tools:
```
sudo apt-get install build-essential checkinstall evolution evolution-dev evolution-data-server evolution-data-server-dev libcurl3-dev libedataserver1.2-dev libebook1.2-dev libecal1.2-dev libedata-book1.2-dev libedata-cal1.2-dev libedataserverui1.2-dev gconf2 gconf2-common libgconf2-4 libgconf11 libgconf2-dev libgconf-dev
```

2. Download and unzip SyncEvolution, then go into the directory.
```
wget "http://easynews.dl.sourceforge.net/sourceforge/sync4jevolution/syncevolution-0.5.tar.gz"
tar -xvf syncevolution-0.5.tar.gz
cd syncevolution-0.5
```

3. Issue configure command.
```
./configure --prefix=/usr
```

4. Compile the program
```
make
```

5. Make a Debian package that can be used to easily manipulate the package. Fill out the information as desired.
```
sudo checkinstall
```

6. Install the package.
```
sudo dpkg -i syncevolution*.deb
```


**CONFIGURATION**

7. Make necessary directories. (Note: You can replace "sync1" with your own string, or leave as is)
```
mkdir ~/.sync4j
mkdir ~/.sync4j/evolution
mkdir ~/.sync4j/evolution/sync1
mkdir ~/.sync4j/evolution/sync1/spds
mkdir ~/.sync4j/evolution/sync1/spds/syncml
mkdir ~/.sync4j/evolution/sync1/spds/sources
mkdir ~/.sync4j/evolution/sync1/spds/sources/addressbook
mkdir ~/.sync4j/evolution/sync1/spds/sources/calendar
mkdir ~/.sync4j/evolution/sync1/spds/sources/todo

```

8. Configuration files (config.txt) will be needed for each of addressbook, calendar, and todo, as well as the syncml file.

```
gedit ~/.sync4j/evolution/sync1/spds/sources/addressbook/config.txt
```
Below is Harty83's configuration. Note that *evolutionsource* should be the name of your calendar, address book or task list in Evolution. If you have a username and password for evolution, then you need to add them under authentication for Evolution source. Otherwise leave the username and password blank as below.

```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = addressbook

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = two-way,slow,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/vcard


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = card3

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```

```
gedit ~/.sync4j/evolution/sync1/spds/sources/calendar/config.txt
```

Harty83's configuration:
```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = calendar

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/calendar


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = cal2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```


```
gedit ~/.sync4j/evolution/sync1/spds/sources/todo/config.txt
```
Harty83's configuration:
```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = todo

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/x-todo


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = task2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```


```
gedit ~/.sync4j/evolution/sync1/spds/syncml/config.txt
```

Fill in the username and password with what is given to you by scheduleworld. You can also customize the device name. Ensure that each device has a unique device name. Harty83's configuration:
```

# the base URL of the SyncML server:
# - Sync4j 2.3
#syncURL = http://hartys.org:1972/egroupware/rpc.php
# - Funambol >= 3.0
#syncURL = http://localhost:8080/funambol/ds
# - sync.scheduleworld.com
syncURL = http://sync.scheduleworld.com/funambol/ds

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = sc-desktop1

# authorization for the SyncML server
username = 
password = 

# set to T to enable an HTTP proxy
useProxy = 0
# proxy URL (http://<host>:<port>)
proxyHost = 
# user agent string used for HTTP
userAgent = SyncEvolution

# full path to directory where automatic backups and logs
# are stored for all synchronizations; if empty, the temporary
# directory "$TMPDIR/SyncEvolution-<username>-<server>" will
# be used to keep the data of just the latest synchronization run
logdir =

# Unless this option is set, SyncEvolution will never delete
# anything in the "logdir". If set, the oldest directories and
# all their content will be removed after a successful sync
# to prevent the number of log directories from growing beyond
# the given limit.
maxlogdirs =

# This value is the number of changes which are sent to the
# server at once. It is set to a very large number to work around
# problems in either client library or server when items are
# actually sent in multiple chunks during a slow sync - do not edit!
maxModPerMsg = 100000

# used by the SyncML library internally; do not modify
begin =0
end =0
firstTimeSyncMode = 0

serverID = 
serverPWD = 
serverNonce = 
clientNonce = 
clientAuthType = 
serverAuthType = 
isServerAuthRequired = 0
proxyPort = 0
proxyUsername = 
proxyPassword = 
checkConn = 0
responseTimeout = 0
readBufferSize = 0
maxMsgSize = 0
encryption = 0

```


**SYNCHRONIZE**
9. You should now be able to synchronize!
```
syncevolution sync1
```

Good luck!

tarek : )

Hi...

I start from fresh installation of ubuntu 7.04.. I follow your indications.. then I type syncevolution sync1 nothig happen... If I type only syncevolution my Personal folders appear.. any suggestions?

---

### Post by reidi on 2007-04-25
> **tareko said:**
> Hello all!

Harty83 provided an excellent howto, but it is a little difficult to follow mindlessly. Extra info also from [Amedee's site]("http://amedee.be/?q=node/4"). Here is a version I think is easier to follow:

*Note*: Tested with Feisty and syncevolution 0.5

**INSTALLATION**
1. Install needed libraries and tools:
```
sudo apt-get install build-essential checkinstall evolution evolution-dev evolution-data-server evolution-data-server-dev libcurl3-dev libedataserver1.2-dev libebook1.2-dev libecal1.2-dev libedata-book1.2-dev libedata-cal1.2-dev libedataserverui1.2-dev gconf2 gconf2-common libgconf2-4 libgconf11 libgconf2-dev libgconf-dev
```

2. Download and unzip SyncEvolution, then go into the directory.
```
wget "http://easynews.dl.sourceforge.net/sourceforge/sync4jevolution/syncevolution-0.5.tar.gz"
tar -xvf syncevolution-0.5.tar.gz
cd syncevolution-0.5
```

3. Issue configure command.
```
./configure --prefix=/usr
```

4. Compile the program
```
make
```

5. Make a Debian package that can be used to easily manipulate the package. Fill out the information as desired.
```
sudo checkinstall
```

6. Install the package.
```
sudo dpkg -i syncevolution*.deb
```


**CONFIGURATION**

7. Make necessary directories. (Note: You can replace "sync1" with your own string, or leave as is)
```
mkdir ~/.sync4j
mkdir ~/.sync4j/evolution
mkdir ~/.sync4j/evolution/sync1
mkdir ~/.sync4j/evolution/sync1/spds
mkdir ~/.sync4j/evolution/sync1/spds/syncml
mkdir ~/.sync4j/evolution/sync1/spds/sources
mkdir ~/.sync4j/evolution/sync1/spds/sources/addressbook
mkdir ~/.sync4j/evolution/sync1/spds/sources/calendar
mkdir ~/.sync4j/evolution/sync1/spds/sources/todo

```

8. Configuration files (config.txt) will be needed for each of addressbook, calendar, and todo, as well as the syncml file.

```
gedit ~/.sync4j/evolution/sync1/spds/sources/addressbook/config.txt
```
Below is Harty83's configuration. Note that *evolutionsource* should be the name of your calendar, address book or task list in Evolution. If you have a username and password for evolution, then you need to add them under authentication for Evolution source. Otherwise leave the username and password blank as below.

```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = addressbook

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = two-way,slow,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/vcard


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = card3

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```

```
gedit ~/.sync4j/evolution/sync1/spds/sources/calendar/config.txt
```

Harty83's configuration:
```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = calendar

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/calendar


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = cal2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```


```
gedit ~/.sync4j/evolution/sync1/spds/sources/todo/config.txt
```
Harty83's configuration:
```

# name of the source, must match the <source> in
# spds/sources/<source>/config.txt
name = todo

# requests a certain synchronization mode:
#   two-way             = only send/receive changes since last sync
#   slow                = exchange all items
#   refresh-from-client = discard all local items and replace with
#                         the items on the server
#   refresh-from-server = discard all remote items and replace with
#                         the items on the client
#   none                = synchronization disabled
sync = two-way

# overrides the supported synchronization modes
syncModes = slow,two-way,refresh-from-client,refresh-from-server

# specifies the format of the data
#
# text/calendar    = Evolution calender data (in iCalendar 2.0 format)
# text/x-todo      = Evolution task data (iCalendar 2.0)
# text/x-vcard     = Evolution contact data in vCard 2.1 format
#                    (works with most servers)
# test/vcard       = Evolution contact data in vCard 3.0 (RFC 2425) format
#                    (internal format of Evolution, preferred with servers
#                    that support it and thus recommended for ScheduleWorld
#                    together with the "card3" uri)
#
# Sending and receiving items in the same format as used by the server for
# the uri selected below is essential. Errors while parsing and/or storing
# items one either client or server can be caused by a mismatch between
# type and uri.
type = text/x-todo


# picks one of Evolution's data sources:
# enter either the name or the full URL
#
# To get a full list of available data sources,
# run syncevolution without parameters. The name
# is printed in front of the colon, followed by
# the URL. Usually the name is unique and can be
# used to reference the data source.
evolutionsource = Personal

# this is appended to the server's URL to identify the
# server's database
uri = task2

# authentication for Evolution source
evolutionuser = 
evolutionpassword = 

# used by the SyncML library internally; do not modify
last = 0

```


```
gedit ~/.sync4j/evolution/sync1/spds/syncml/config.txt
```

Fill in the username and password with what is given to you by scheduleworld. You can also customize the device name. Ensure that each device has a unique device name. Harty83's configuration:
```

# the base URL of the SyncML server:
# - Sync4j 2.3
#syncURL = http://hartys.org:1972/egroupware/rpc.php
# - Funambol >= 3.0
#syncURL = http://localhost:8080/funambol/ds
# - sync.scheduleworld.com
syncURL = http://sync.scheduleworld.com/funambol/ds

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = sc-desktop1

# authorization for the SyncML server
username = 
password = 

# set to T to enable an HTTP proxy
useProxy = 0
# proxy URL (http://<host>:<port>)
proxyHost = 
# user agent string used for HTTP
userAgent = SyncEvolution

# full path to directory where automatic backups and logs
# are stored for all synchronizations; if empty, the temporary
# directory "$TMPDIR/SyncEvolution-<username>-<server>" will
# be used to keep the data of just the latest synchronization run
logdir =

# Unless this option is set, SyncEvolution will never delete
# anything in the "logdir". If set, the oldest directories and
# all their content will be removed after a successful sync
# to prevent the number of log directories from growing beyond
# the given limit.
maxlogdirs =

# This value is the number of changes which are sent to the
# server at once. It is set to a very large number to work around
# problems in either client library or server when items are
# actually sent in multiple chunks during a slow sync - do not edit!
maxModPerMsg = 100000

# used by the SyncML library internally; do not modify
begin =0
end =0
firstTimeSyncMode = 0

serverID = 
serverPWD = 
serverNonce = 
clientNonce = 
clientAuthType = 
serverAuthType = 
isServerAuthRequired = 0
proxyPort = 0
proxyUsername = 
proxyPassword = 
checkConn = 0
responseTimeout = 0
readBufferSize = 0
maxMsgSize = 0
encryption = 0

```


**SYNCHRONIZE**
9. You should now be able to synchronize!
```
syncevolution sync1
```

Good luck!

tarek : )

I believe the same error appears in each of the three sources config.txt files above:  refresh-from-server= and refresh-from-client= are associated with each other's definition.  

Anybody?

---

### Post by xand on 2007-05-02
Alright Feisty has now fixed the segmentation fault messages i used to get,  and now i'm able to sync everything i've always wanted to. :guitar: 

Great tutorials, keep the good work guys.

---

### Post by maddentim on 2007-05-04
Ok, I have it all set up and it works fine with one festering exception.  For repeating events that were originated in evolution, when they get synced to scheduleworld and google, they do not show up in scheduleworld but are 5 hours off (early) the correct time.  Now, I am 5 hours off GMT, so I am suspecting that is the problem, but I do not know how to deal with it. 

Has anyone else experienced this, or read about it?

---

### Post by PsychoKlown on 2007-05-11
I'm getting a similar error as the server-data, but this one says that there isn't a backend enabled.

```
checking pkg-config is at least version 0.9.0... yes
checking for EPACKAGE... yes
checking for ECAL... no
checking for ECAL... no
checking for ECAL... no
checking for EBOOK... no
checking for EBOOK... no
checking for EBOOK... no
configure: error: no backend enabled - refusing to continue: 
Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libedataserver, libecal and libebook (the
latter two are optional).

```

Thanks
I attached my pkg-config list.

---

### Post by serendipity4u on 2007-05-15
In order to compile the syncevolution package a buch of libs are required.

I found a complete explanation at [http://doc.ubuntu-fr.org/syncevolution:](http://doc.ubuntu-fr.org/syncevolution:)
[LIST][COLOR="Blue"][*]sudo apt-get install linux-headers-`uname -r` build-essential fakeroot checkinstall g77 libcurl3-dev evolution-data-server-dev
[*]sudo apt-get install libedata-cal1.2-dev libedata-book1.2-dev libebook1.2-dev libedataserver1.2-dev libecal1.2-dev[/COLOR]
[/LIST]

After that proceed with [COLOR="Blue"]./configure --prefix=/usr
make[/COLOR] - this should solve the no backend enabled error.

---

### Post by PsychoKlown on 2007-05-15
Thanks serendipity4u!

Now my problem is :
```
01:52:11 GMT -0700 [ERROR] - no syncURL configured - perhaps the server name "gilbert" is wrong?
01:52:11 GMT -0700 [ERROR] - cannot proceed without configuration

```

---

### Post by wessel_k on 2007-05-20
Hi,

I hope somebody can help me out here. syncevolution works like a charm. It syncs everything except for one thing. 
When somebody has a home/private address in egroupware, it seems that it's not synced. Can anybody help me out there, so that it will sync. I can't seem to find anything about it. Or maybe point me in the right direction where to pose the question.

Regards,

Wessel

---

### Post by maddentim on 2007-05-23
Does anyone know how to sync multiple calendars in Google to a corresponding set of multiple calendars in Evolution?  I have my personal calendar and then a family calendar.  I want to keep them apart, but have the sync.  I am thinking that I would need to set up a second ScheduleWorld account to handle.  I am not seeing where you can have multiple calendars in ScheduleWorld.  Anyone have any experience here??

Thanks!

---

### Post by Kevanx on 2007-06-20
I hope people are still reading this, as I ran into an error that doesn't seem to be documented.

Upon using
 ```
SyncEvolution one
```

I get:

```
[ERROR] - calendar: access to calendars not compiled into this binary, text/calendar not supported

Synchronization failed, see /tmp/SyncEvolution-kevan-one/client.log for details.
```

I don't know where to begin on this one, so any suggestion would be greatly appreciated, and thanks for everyone's hard work on this remarkable tutorial.

*Solved: I uninstalled v0.6pre2 and used v0.5, and it worked perfectly.*

---

### Post by rlundy82 on 2007-06-22
Hello everyone, this thread has been incredibly helpful so far, but despite its best efforts, I'm still getting a problem.

Here is the error I'm getting when I run syncevolution

```
$ syncevolution site
09:55:09 GMT -0400 [ERROR] - Error in sync() - configuration not set correctly.
09:55:09 GMT -0400 [ERROR] - sync failed without an error description, check log

Synchronization failed, see /tmp/SyncEvolution-rlundy-site/client.log for details.

Modifications:
```
So I try
```

$ cat /tmp/SyncEvolution-rlundy-site/client.log
09:55:09 GMT -0400 [ERROR] - Error in sync() - configuration not set correctly.
09:55:09 GMT -0400 [DEBUG] - Writing configuration settings to the management tree
09:55:09 GMT -0400 [ERROR] - sync failed without an error description, check log
```

And on outlook, I'm getting the following when I try to use the syncml plugin

```
2007-06-22 10:56:53:281 - # SyncClient API Native Log

10:56:53:281 [INFO] - Initializing

10:56:54:375 [INFO] - *********** CONTACTS SYNC ***********

10:56:55:359 [ERROR] - HttpSendRequest Error: 12029

10:56:55:359 [INFO] - Error connecting to the server.
```

which leads me to believe theres something wrong with server

---

### Post by thierrybo on 2007-07-22
Hi,

well, this is more a general linux question but about syncevolution. I just installed 0.6pre2 on a new ubuntu setup (0.5 was installed before). Do we need to keep all dependencies installed  after compiling syncevolution. Are there some packets needed only at compile time and some other only at run time ?

---

### Post by reidi on 2007-07-22
> **tareko said:**
> Hello all!

Harty83 provided an excellent howto, but it is a little difficult to follow mindlessly. Extra info also from [Amedee's site]("http://amedee.be/?q=node/4"). Here is a version I think is easier to follow:



Hey is necessary to keep all the packages and libraries that are installed up front ("apt-get install a_whole_bunch_of_stuff")  after the package is built and installed?  Can they be removed ?

---

### Post by SmudgeTheFirst on 2007-07-30
> **maddentim said:**
> Does anyone know how to sync multiple calendars in Google to a corresponding set of multiple calendars in Evolution?  I have my personal calendar and then a family calendar.  I want to keep them apart, but have the sync.  I am thinking that I would need to set up a second ScheduleWorld account to handle.  I am not seeing where you can have multiple calendars in ScheduleWorld.  Anyone have any experience here??

Thanks!

I'm having trouble seeing how this would work as well. I may just end up making a second ScheduleWorld account. It seems to be the fastest workaround.

---

### Post by adnup1 on 2007-07-30
Hi @all, 

first of all...   I'm new to Linux and all of it.
I tried getting a lot of tools to run and most of it worked well. 

But with the syncevolution-stuff I really have my troubles...

I'm using Ubuntu 7.04 and tried getting syncevoltution 0.5 and 0.6 to work 
with my Evolution. 

When I'm trying to sync ADDRESSBOOK with   =>   syncevolution sync1  <=  
then nothing happens. 

When I leave the Adressbook stuff and only try to sync Todo and Calendar, 
then i works for the first time and after that it creates "wrong URI" Errors and
jumps back to SLOW mode instead of TWO-WAY !

What do i do wrong ???

Thanks
Adnup1

---

### Post by schmickers on 2007-07-31
Is there any way to use SyncEvolution to sync more than one calendar to the funambol or scheduleworld server?

---

### Post by thierrybo on 2007-08-01
Hi,

I think for the moment it is not possible to sync the SAME evolution calendar with multiple calendars. However if you have** several** Evolution calendars and **several** ScheduleWorld accounts, you just need to follow the first page guidelines (post #4) of this thread and create a new /home/*your_home*/.sync4j/evolution/**NewWhatever**/spds directory structure, ie. create a new **NewWhatever**/ directory structure.

Create a new** config.txt** in the /home/*your_home*/.sync4j/evolution/**NewWhatever**/spds/syncml directory and fill the new account settings and so on. 

In /home/*your_home*/.sync4j/evolution/**NewWhatever**/spds/sources create only a *calendar* directory (you could  synchronize a second adressbook also) and set your config.txt according to you needs with the new calendar.

Then if you want to synchronize both simultaneously just create a shell script that run :

syncevolution whatever
syncevolution NewWhatever

---

### Post by olskar on 2007-08-03
askar@barbara:~$ syncevolution ok
Segmenteringsfel (core dumped)

why?

---

### Post by tikey on 2007-08-09
I have the same problem. I tried with version 0.5 and 0.6 several times. I installed all the required packages in advance and tried it over and over again. There is no error message during the configure and none during the make. It installs the package and I can run syncevolution without argument. I then get the address books, calendars and task lists.
But when I try to run with syncevolution scheduleworld I get the
Segmentation fault (core dumped)

Does anyone have an idea what that might be? Is it more likely that something went wrong during the make process or could it simply be some error in one of the config.txt? Or something completly different?

Any help would be appreciated.

good night
   tikey

edit: I tried it again now. Differences: I edited the config-files with nano instead of kate and I called the directory sync1 instead of scheduleworld. I have seriously no idea if that can be the reason but now it works!

edit2: Ok, that was to early. It worked only a few times. I was trying some things but didn't change anything in the configuration. I only created some events in the evolution calendar (with kontact) tried to sync and it worked. I then created an event in google calendar, synced it with scheduleworld and then tried to run syncevoltion. I now get the segmentation fault again. Isn't that weired???

---

### Post by gamera06 on 2007-08-26
Hi Everyone,

I got Ubuntu 7.04, GCal account, scheduleworld account and syncing with Gcal, SyncEvolution installed and seems to work (I don't have any errors if I execute 'syncevolution gcal' in a shell.

I don't get anything in the calendar view from scheduleworld.
The calendar was first set up using the iCal link from GCal (one way sync), so it has been changed to:
webcal://www.ScheduleWorld.com/sw/webDAVDir/myid.ics
(myid is showing my login).

Any idea ?

---

### Post by Dvad78 on 2007-08-30
I think i figured out a workaround for the segment fault! (Im using Ubuntu Feisty)

After much poking and prodding, i have found that using ScheduleWorlds standard syncml works! all you have to do is edit your sources config.txt files to point to the right ones. 

under /sources/calendar/config.txt  change ```
uri = cal2 
``` to ```
uri = cal
```
under /sources/addressbook/config.txt  change ```
uri = card3 
``` to ```
uri = card
```
under /sources/todo/config.txt  change ```
uri = task2 
``` to ```
uri = task
```

After making these changes everything synced wonderfully for me! :guitar:

---

### Post by maddentim on 2007-09-10
Hello.
Has anyone upgraded from syncevo 0.5 to 0.6? I notice a new version was out there.  Just curious.  I have some issues with time zones and recurring events and am hoping that it may be resolved in the new version...

---

### Post by nelio2k on 2007-09-25
Hi all,

I have syncevolution v 0.6. Whenever I try to run it, I get:

syncevolution: error while loading shared libraries: libedataserver-1.2.so.7: cannot open shared object file: No such file or directory

I've made sure the packages that I needed are installed. I downloaded the binaries from syncevolution's site, and copied the binary files over to /usr/local/bin/

I have libedataserver packages installed. What else am I doing wrong?

thank you.

---

### Post by High Camp on 2007-10-10
Hi All

I've installed Syncevoltuion. It seems like a great idea but I have yet to get it running and I'm hoping someone can give me a hand.

First I tried what dvad suggested and change the entries to uri = card, etc. I even tried 0, 1, 2, and 3 there as well with no luck. 

I think the key errors come at the end of the terminal output:
```
14:50:01 GMT -0700 [ERROR] - Server Failure: server returned error code -1
14:50:01 GMT -0700 [ERROR] - Error in syncing: Server Failure: server returned error code -1
14:50:01 GMT -0700 [ERROR] - sync failed without an error description, check log

Synchronization failed, see /tmp/SyncEvolution-simon-simon/client.log for details.

Modifications:
*** addressbook ***
no changes
*** calendar ***
no changes
*** todo ***
no changes
```

I have attached my error log and the terminal output and I will much appreciate any help anyone can provide. Thanks much.

---

### Post by capturesteve on 2007-10-13
> **harty83 said:**
> make sure you have evolution-data-server-dev installed.
I've done this like three times and it says i already have the latest version when i try to install it, but i still get this error 

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EPACKAGE... checking for EPACKAGE... checking for EPACKAGE... configure: error: No compatible evolution-data-server was found.

Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libecal, libedata, evolution-data-server
and libedataserver.

You can check that these packages are available by running
pkg-config --list-all.

---

### Post by HermanAB on 2007-10-13
If you want a groupware system that Just Works (TM), then get Citadel:
[http://www.citadel.org](http://www.citadel.org)

It takes about 20 minutes to install it using their Easy Install script, a little more to add spam assassin and clamav.

The reason it just works, is because at its core, it is really very old, dating back to about 1982, so the bugs have been worked out 20 years ago already.

Cheers,

H.

---

### Post by capturesteve on 2007-10-13
But do you have any ideas why, when i run ./configure it is acting like i do not have evolution-data-server and evolution-data-server-dev installed?

---

### Post by elektronaut on 2007-10-14
> **HermanAB said:**
> If you want a groupware system that Just Works (TM), then get Citadel:
[http://www.citadel.org](http://www.citadel.org)

Citadel has been mentioned in the first post of this thread. Apparently no SyncML, so it wouldn't help me synchronizing the contact list in my mobile phone with my PIM. Which is the most important point for me. The web access is just an add-on for me.

---

### Post by KenSentMe on 2007-10-17
> **capturesteve said:**
> But do you have any ideas why, when i run ./configure it is acting like i do not have evolution-data-server and evolution-data-server-dev installed?

Install some other packages:

```

sudo apt-get install libedataserver1.2-dev libebook1.2-dev libecal1.2-dev 

```

---

### Post by evets on 2007-10-19
I've been looking at [[COLOR="Blue"]Simple Groupware[/COLOR]]("http://simple-groupware.org") , it looks ***very*** good, and has fairly complete docs included. Yesterday, I had a question and emailed the author, he responded in 3 minutes! 

Unless I hear something negative about it, I'm going to test it as soon as I finish with the one I am testing right now.

---

### Post by High Camp on 2007-10-27
Hi All

Has anyone ever seen an error like this:
```
simon@simon:~$ syncevolution simon
Segmentation fault (core dumped)
```

And if so, any idea what's causing it?

I've been emailing with the Syncevolution users list and they are having a hard time figuring it out too.

Any help is much appreciated,

---

### Post by maddentim on 2007-10-28
High camp: I have not seen this error.  I did a quick google search on syncevolution segmentation fault (core dumped) and found several results that seemed to potential to explain the problem.  I don't have time to do this research for you, but if I were you I would browse those and see if there were some that applied to your situation.  Some of them seemed to be focused on how syncevolution was compiled.  Since syncevolution is not a mantained Ubuntu package, I could see where this might come into play.  Have you done any upgrades lately or stuff like that?  How did Syncev get on your system?  Etc.

---

### Post by High Camp on 2007-10-29
Apparently this is an Evolution bug. I was told there is a bug report on the Gnome Bugzilla but I have yet to find it. There are a whole bunch of bug reports on there about it crashing with "Segmentation Fault". This occurs in Evolution 2.12 so I think everyone will probably start seeing it as they upgrade to Gutsy.

I guess all I can do is wait for them to fix the bug unless I want to learn the code and try myself.

If anyone comes across a fix I would love to hear it.

Also, if anyone has any info on how to get the debug info from Evolution I would love to figure that out too.

---

### Post by maddentim on 2007-10-29
I am on Gutsy now for almost a week and running syncevolution.  Have not seen this bug (yet! how it does not bite me!)

---

### Post by maddentim on 2007-10-29
Evets: Have not heard of this Simple Groupware previously.  Now that I have syncev working, I have not looked around much.  Let us know how it goes...

---

### Post by High Camp on 2007-10-29
> **maddentim said:**
> I am on Gutsy now for almost a week and running syncevolution.  Have not seen this bug (yet! how it does not bite me!)

I'm guessing you did the upgrade and did not upgrade Evolution. You are probably still on 2.8 (I think). If you do a fresh install you get version 2.12 and that is were the bug bites (I think). I'm actually considering downgrading Evolution because I desperately need to be able to sync my palm and my online calendars. Before I used Yahoo and Itellasync.

Aaaarrrrggggg.

---

### Post by maddentim on 2007-10-30
I did an upgrade.  However, according to Synaptic, my evolution is at version 2.12 (but the about screen in evo shows 2.8...  Not sure what the 2.8 refers too....

---

### Post by jpastore on 2007-11-06
I used harty83's post from 2005 and everything worked fine.

I did a dist-upgrade from feisty and everything seems to work...

now if only I could sync my Nokia 9500...stuck on syncing to outlook and outlook to schedule world to evolution...

That's probably the last thing I need to get rid of windows...and maybe play with spam assassin. I rely heavily on Cloud Mark's Spamnet. 

-Jon

---

### Post by jpastore on 2007-11-07
it's not fair...just as I posted this message...the very next day I get segmentation faults with syncevolution after an update ...

/sigh

---

### Post by cartisdm on 2007-11-14
Ok, followed the tutorial and it seems to work like a charm (pretty idiot proof).  However, I can't seem to sync entirely how I'd like it to.  If I add something to the calendar on the scheduleworld and run the sync, it shows up in Evolution perfectly.  If I add something in Google calendar, it shows up in schedule world perfectly.  However, events transfered from google calendar onto scheduleworld do not transfer at all to my Evolution calendar.  What am I doing wrong?

Here is an email I get every time I sync...
> Sync with Google failed:Token invalid - AuthSub token has wrong scopenull: HTTP/1.1 401 Token invalid - AuthSub token has wrong scope, WWW-Authenticate: AuthSub realm="https://www.google.com/accounts/AuthSubRequest", Cache-control: private, Date: Wed, 14 Nov 2007 06:10:34 GMT, Content-Length: 213, Content-Type: text/html; charset=UTF-8, Server: GFE/1.3, 

---

### Post by High Camp on 2007-11-24
Many thanks to Patrick at Synevolution for this.

Patrick and I emailed back and forth many times about the "segfault" error. It turns out for me this was caused by not having a line break at the end of all the config.txt files. I literally went in, went to the bottom, hit enter, and saved. Now everything works fine. For any n00bs out there keep in mind that some text editors remove line breaks at the end of files.

Thanks agian to Patrick and I hope no one else makes this mistake.

---

### Post by cartisdm on 2007-11-29
still getting the same error, however, my calendar is syncing with someone else's calendar......I copied and pasted all the codes from the guide for setting this up, does that matter?

---

### Post by facted on 2008-01-09
Before I go through with all of this, I'd just like to make sure this works for my particular situation. I have a Palm 700p that I'd like to sync with google calendars in Ubuntu. I have set up schedule world with my separate calendars and now I'm trying to set up evolution. My multiple google calendars all sync to my Palm with different categories. However, in evolution, when I sync my palm, all my events go straight to one category rather than remaining segregated. 

Is it possible using evolution and schedule world to keep my calendars separated and sync with Palm?

Thanks.

---

### Post by bnrbnsn on 2008-02-09
I have a suggestion for those who wish to simplify the process a bit.  (If it doesn't work, you can always just uninstall the installed packages using System > Administration > Synaptic Package Manager.)

1. Go to [http://www.estamos.de/download/apt/](http://www.estamos.de/download/apt/)
2. Read the README for directions on installing using an apt-based system (such as Ubuntu).

Also, if you have further questions, referring to the project homepage may be handy: [http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/)

---

### Post by wersdaluv on 2008-02-28
This is amazing! I have a Sony Ericsson P990i. I managed to sync it with scheduleworld. I already have syncevolution installed but I dont know how to sync Evolution with Scheduleworld. What do I do next? :)

---

### Post by wersdaluv on 2008-03-01
Okay. I tried to do it. Whenever I **syncevolution whatever**, I get
```
Segmentation fault (core dumped)
```

What should I do now? :)

---

### Post by highmighty on 2008-03-05
Solved

---

### Post by highmighty on 2008-03-05
Hi all Linux users!

I think I'm almost getting it to work :-)

But I'm stuck at the very last step, the "whatever" part, what should be my "whatever" name?  Bare with me plz, I'm an Ubuntu newbie here :)

Thank you all for your time!

I can't wait to sync all my data with Evolution!

highmighty

> 

Now to run, do 
```
syncevolution *whatever*
```

with the whatever being what you named /home/*your_home*/.sync4j/evolution/*whatever*

That should do it.  Let me know if you have any problems.



---

### Post by FokkerCharlie on 2008-05-02
Splendid!

Works great with my new w960i vs Evolution.

Kudos to everyone involved with this.

For what it's worth:

I installed SyncEvolution from the repositories (it was the only one of 3 versions on offer that would install via synaptic), and followed the instructions on page 5 (ish)

Thanks again
Charlie

---

### Post by theZoid on 2008-05-08
> **FokkerCharlie said:**
> Splendid!

Works great with my new w960i vs Evolution.

Kudos to everyone involved with this.

For what it's worth:

I installed SyncEvolution from the repositories (it was the only one of 3 versions on offer that would install via synaptic), and followed the instructions on page 5 (ish)

Thanks again
Charlie

What name was it under in synaptic?  thanks

---

### Post by FokkerCharlie on 2008-05-20
Look for syncevolution-evolution-2.12 

Worked for me.

Cheerio
Charlie

---

### Post by FokkerCharlie on 2008-05-21
Can anyone help with this?  Couldn't find anything about it in this thread-

I've just discovered that when I sync my calendar, there seems to be a problem with time zones- all the entries in my phone come out 4 hours earlier than in Evolution!  Eg a 1115 appointment in Evo translates to 0715 in the phone.  And I get very crotchety if I have to see people that early...

Time zone in Evolution seems to be right, as does the time zone in the phone.

Any suggestions?

Cheers
Charlie

---

### Post by theZoid on 2008-05-21
I ended up sync'ing my blackberry to SW via funambol OTA, then Thunderbird OTA via SW extensions....works well, quick set up...

---

### Post by Fredo on 2008-06-18
For those of you who had troubles setting up syncevolution: I wrote a small GTK frontend for syncevolution that features a setup assistant. I mainly wrote it for myself, but it might be helpful for others, too. You can check it out here: [https://launchpad.net/genesis-sync](https://launchpad.net/genesis-sync)

Any feedback is appreciated. And if you want to improve Genesis, send me your patches... :-)

Cheers,
Fredo

---

### Post by FokkerCharlie on 2008-06-18
Nice one, Fredo

However, I can't seem to run it!  I'm not even sure which file I should be executing...  could you give us a clue?

I was thinking the other day that we need a GUI for this, so I'm glad you've arrived!

Charlie

---

### Post by Fredo on 2008-06-18
Oh, yes, sorry. I guess I should update the README file.

The 0.3 release now features an install script. You should be able to install it with "sudo python setup.py install" in the directory that contains the setup.py file. Then you can start it from the menu (unter Accessories)  or from the command line with "genesis".

If you encounter any problems, please tell me. If you think it's a bug, please file it on the bug tracker on launchpad.

Fredo

---

### Post by FokkerCharlie on 2008-06-18
Hi Fredo, thanks for the update.

I installed genesis, that part looked OK- none of the feedback looked like an error to me at least.  Unfortunately, it won't run on my laptop- here's the output:

```
charlie@charlie-laptop:~$ genesis
Traceback (most recent call last):
  File "/usr/bin/genesis", line 20, in <module>
    import Genesis.genesis as genesis
  File "/usr/lib/python2.5/site-packages/Genesis/genesis.py", line 71, in <module>
    '/org/freedesktop/NetworkManager')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
```


I should mention, too- the dependencies you mention don't all show up in Synaptic for me.  I could not find pyGTK, but do have Python-GTK2 installed.  I have libnotify1 instead of libnotify for the same reason.

I don't know if this is the right way to work arond this, but it could well be part of the problem!

Cheers
Charlie

---

### Post by Fredo on 2008-06-18
> **FokkerCharlie said:**
> 
```
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
```


Ok, it seems that you don't have networkmanager started. Genesis asks NM for a working connection before syncing to avoid sync failures because of connection problems.

I do now handle this case and simply assume a working connection when NM is not available. I uploaded a new release (0.3.1) that contains the fix. Could you please test it? Since I don't want to remove networkmanager I can't actually try my fix out... :-)

> **FokkerCharlie said:**
> 
I should mention, too- the dependencies you mention don't all show up in Synaptic for me.  I could not find pyGTK, but do have Python-GTK2 installed.  I have libnotify1 instead of libnotify for the same reason.

Yes, the README file listed the library names, not the package names. I now updated the README file to explain the installation and list the package names. You'll find it in the new release tarball.

I hope you finally get this working, as for now I caused you more trouble than help...

Cheers,
Fredo

---

### Post by FokkerCharlie on 2008-06-18
Hi Fredo

Well, that seems to work!  Very many thanks for your contribution here.  I am sure that a lot of people will find this helpful.  I think that the previous problem was associated with my preference for Wicd over Network Manager.

Am I right in thinking that the utility presently can only create new profiles, and not edit them?

Thanks again, good show!
Charlie

---

### Post by Fredo on 2008-06-18
Hi Charlie,

> **FokkerCharlie said:**
> Well, that seems to work!  Very many thanks for your contribution here.  I am sure that a lot of people will find this helpful.  I think that the previous problem was associated with my preference for Wicd over Network Manager.

I'm glad to hear that. And yes, since I do use NetworkManager, I didn't take care of situations where this is not the case. I'm glad that this is fixed now, even though NM users are still a bit in advantage.

> **FokkerCharlie said:**
> Am I right in thinking that the utility presently can only create new profiles, and not edit them?

Yes, that's true. Genesis was mainly designed to get people started without all the hassle of editing configuration files. An advanced configuration editor with the possibility to edit profiles and access more exotic options that aren't available in the Wizard is still on the todo list. And I'm not very optimistic that I'll find the time to actually implement it - since it's much work for only little benefit.

But - as always - if anyone does find this useful and is willing to contribute to the project, I'd be more than glad to integrate patches.

Cheers,
Fredo

---

