---
title: "Vnstat error on installing"
date: 2019-11-06
forum: General Help
---

### Post by lumaja2 on 2019-11-06
I am using Ubuntu 16.04. When I'm trying to install `vnstat` by running:
 
 
     sudo apt-get install vnstat
 
 
 I get the following error:
 
 
     Error “E: Sub-process /usr/bin/dpkg returned an error code (1)”  
 
 
 
 
 Can someone help me fix this?

---

### Post by guiverc on 2019-11-06
You'll have to read further up in the messages to see the problem. That message is a summary hinting for you to look back to see the real error message (ie. look at the message from the sub-process that caused the return value to be set to 1)

---

### Post by lumaja2 on 2019-11-06
Output that for the command sudo apt install vnstat
  	 	 	 	    ```
luis@luis-desktop:~$ sudo apt install vnstat
  [sudo] password for luis:  
  Reading package lists... Done
  Building dependency tree        
  Reading state information... Done
  Suggested packages:
    vnstati
  The following NEW packages will be installed:
    vnstat
  0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
  2 not fully installed or removed.
  Need to get 0 B/74.1 kB of archives.
  After this operation, 237 kB of additional disk space will be used.
  Selecting previously unselected package vnstat.
  (Reading database ... 261633 files and directories currently installed.)
  Preparing to unpack .../vnstat_1.14-1ubuntu2_amd64.deb ...
  Unpacking vnstat (1.14-1ubuntu2) ...
  Processing triggers for man-db (2.7.5-1) ...
  Processing triggers for systemd (229-4ubuntu21.22) ...
  Processing triggers for ureadahead (0.100.0-19.1) ...
  ureadahead will be reprofiled on next reboot
  Setting up postfix (3.1.0-3ubuntu0.3) ...
  setting myhostname=luis-desktop in /etc/postfix
  
 
  Postfix is now set up with the changes above.  If you need to make changes, edit
  /etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
  values, see postconf(1).
  
 
  After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

   	 	 	 	   
 Running newaliases
  newaliases: fatal: myorigin parameter setting must not contain multiple values: luis-deskto [email]ljacinto2501@gmail.com[/email]
  dpkg: error processing package postfix (--configure):
   subprocess installed post-installation script returned error exit status 75
  dpkg: dependency problems prevent configuration of bsd-mailx:
   bsd-mailx depends on default-mta | mail-transport-agent; however:
    Package default-mta is not installed.
    Package postfix which provides default-mta is not configured yet.
    Package mail-transport-agent is not installed.
    Package postfix which provides mail-transport-agent is not configured yet.
  
 
  dpkg: error processing package bsd-mailx (--configure):
   dependency problems - leaving unconfigured
  No apport report written because the error message indicates its a followup error from a previous failure.
                            Setting up vnstat (1.14-1ubuntu2) ...
  Processing triggers for libc-bin (2.23-0ubuntu11) ...
  Processing triggers for systemd (229-4ubuntu21.22) ...
  Processing triggers for ureadahead (0.100.0-19.1) ...
  Errors were encountered while processing:
   postfix
   bsd-mailx
  E: Sub-process /usr/bin/dpkg returned an error code (1)
  luis@luis-desktop:~$  
 
```

---

### Post by dragonfly41 on 2019-11-06
[https://phoenixnap.com/kb/fix-sub-process-usr-bin-dpkg-returned-error-code-1](https://phoenixnap.com/kb/fix-sub-process-usr-bin-dpkg-returned-error-code-1)

---

