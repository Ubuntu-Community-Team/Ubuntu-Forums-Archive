---
title: "Unable to move mongodb database from SSD to HD"
date: 2019-11-11
forum: General Help
---

### Post by makem2 on 2019-11-11
My OS is:

```

makem@ssdTOSH:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04.3 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.3 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic
makem@ssdTOSH:~$

```

I have the latest mongodb installed, running and tested with dummy data on the main OS which is on an SSD

This SSD is relatively small when compared to other HD's I have so I want to move the database data to another drive. What appeared simple is proving not to be.

I first created a new folder /new_drive/data and copied to it the default mongodb data file.

I have tried stopping mongodb and using the start command with the new dbPath but I get the error:

```

makem@ssdTOSH:~$ 
sudo service mongod stop
sudo service mongod start --dbPath /new_drive/data/mongodb
mongo
MongoDB shell version v4.2.1
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
2019-11-11T19:18:57.038+0000 E  QUERY    [js] Error: couldn't connect to server 127.0.0.1:27017, connection attempt failed: SocketException: Error connecting to 127.0.0.1:27017 :: caused by :: Connection refused :
connect@src/mongo/shell/mongo.js:341:17
@(connect):2:6
2019-11-11T19:18:57.040+0000 F  -        [main] exception: connect failed
2019-11-11T19:18:57.040+0000 E  -        [main] exiting with code 1
makem@ssdTOSH:~$

```

To sure the database is running, because I know one reason for the error is that is is not running:

```

makem@ssdTOSH:~$ sudo service mongod start
[sudo] password for makem: 
makem@ssdTOSH:~$ mongo
MongoDB shell version v4.2.1
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
2019-11-11T19:53:59.135+0000 E  QUERY    [js] Error: couldn't connect to server 127.0.0.1:27017, connection attempt failed: SocketException: Error connecting to 127.0.0.1:27017 :: caused by :: Connection refused :
connect@src/mongo/shell/mongo.js:341:17
@(connect):2:6
2019-11-11T19:53:59.136+0000 F  -        [main] exception: connect failed
2019-11-11T19:53:59.136+0000 E  -        [main] exiting with code 1
makem@ssdTOSH:~$ 

```

I have also tried (with the above start command), editing the /etc/mongodb.conf to suit the new path but get the same error.

I have tried using a symlink, again with the same error.

So, my conclusion is, I am doing something wrong but cannot see what. Help?

---

### Post by The Cog on 2019-11-11
For a start, have a look at /var/log/mongodb/mongodb.log and see if there is anything useful in there.

---

### Post by makem2 on 2019-11-11
> **The Cog said:**
> For a start, have a look at  /var/log/mongodb/mongodb.log and see if there is anything useful in  there.

The log contains:

Detected unclean shutdown - /new_drive/data/mongodb/mongod.lock is not empty

Detected data files in /new_drive/data/mongodb/ created by the 'wiredTiger' storage engine, so setting the active storage engine to 'wiredTiger'

Failed to start up WiredTiger under any compatibility version.
Reason: 1: Operation not permitted
Fatal Assertion 28595 at src/mongo/db/storage/wiredtiger/wiredtiger_kv_engine.cpp 786

***aborting after fassert() failure

The log contains a lot more but those are noted as error. The log does not wrap so I cannot post it all. I notice that the log contains the correct --dbPath.

Edit: I believe I have been using the wrong start/stop commands so have set everything back to a working mongodb on the SSD. If you can see an error (apart from the incorrect start.stop commands) I would appreciate it.

sudo systemctl start mongodb
sudo systemctl stop mongodb
   	 	 	 	 	 	    [TABLE]
 	 	[TR]
 		[TD="align: left"][/TD]
 	[/TR]
 [/TABLE]

---

