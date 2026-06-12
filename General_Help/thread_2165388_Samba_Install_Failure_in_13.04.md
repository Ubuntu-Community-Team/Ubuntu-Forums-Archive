---
title: "Samba Install Failure in 13.04"
date: 2013-08-04
forum: General Help
---

### Post by mcman56 on 2013-08-04
I'm trying to load Samba in 13.04.  I get a failure notice at the end of the loading process.  If I then try to run Samba, there is another failure message.   I found a link to a bug report so does this mean it simply will not work on my machine or is there a work around?
Gateway NE71B laptop

_**Bug report**_
[https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1194548](https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/1194548)

**_load error_**
  	 	 	 	   dpkg: error processing samba4 (--configure): 
  subprocess installed post-installation script returned error exit status 255 
 Processing triggers for libc-bin ... 
 ldconfig deferred processing now taking place 
 Processing triggers for ureadahead ... 
 Processing triggers for ufw ... 
 Errors were encountered while processing: 
  samba4 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 

**_Run error_**
  	 	 	 	   
dan@dan-NE71B:~$ samba 
 samba: /usr/lib/x86_64-linux-gnu/libwbclient.so.0: no version information available (required by /usr/lib/x86_64-linux-gnu/samba/libauth4.so) 
 [2013/08/04 15:20:32,  0] ../lib/util/debug.c:592(reopen_logs_internal) 
   Unable to open new log file '/var/log/samba/log.%m': Permission denied 
 [2013/08/04 15:20:32,  0] ../source4/smbd/server.c:369(binary_smbd_main) 
   samba version 4.0.0 started. 
   Copyright Andrew Tridgell and the Samba Team 1992-2012

---

### Post by zteam2 on 2013-08-04
Is there any particular reason why you need Samba 4?
The samba 4 packages is experimental versions of Samba, and it is not considered stable as the package description says.


So based on that my advice would be to stick with the original samba package instead unless you really need som new features only available in Samba 4.

If you really want to use Samba 4, you can probably, get that by using some ppa (just Google for Ubuntu 13.04 samba 4 ppa)

But if you just wanna share files  or printers with other computers in the network just stick with the original package instead.

---

### Post by mcman56 on 2013-08-04
I don't care about the version but followed the only instructions I could find for 13.04 that worked. See the link.  Nothing seemed to happen when loading from the Software Center.  However, there are so many Samba packages/ options maybe I simply could not figure out just what needs to be loaded.  Is there any place to find some instructions?  Last time I did this was in Lubuntu and it just took 2 packages from that software center. 

[http://askubuntu.com/questions/303818/samba-is-not-working-on-ubuntu-13-04](http://askubuntu.com/questions/303818/samba-is-not-working-on-ubuntu-13-04)

---

### Post by zteam2 on 2013-08-06
You can just right-click on  a folder and Ubuntu, will should ask you if you want to install Samba automatically for you.

I'm not sure if that would work for you, now, that you already have installed some samba-packages but you can always try :-)

If you have the samba and samba common packages installed it should work.

---

### Post by mcman56 on 2013-08-11
My solution was to go back to 12.04

---

