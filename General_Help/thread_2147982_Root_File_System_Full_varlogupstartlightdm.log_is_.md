---
title: "Root File System Full /var/log/upstart/lightdm.log is 9.8 gb"
date: 2013-05-23
forum: General Help
---

### Post by azdavef on 2013-05-23
When I booted this morning I got a Root File System Full notice and after snooping around I found that my /var/log/upstart/lightdm.log was 9.8 gb, which I suspect is the cause.  Can I just delete this file?  I think I should try to find out why it is so large, too.  I have no idea how to do this.  Thanks in advance for the help.  I am running 12.04 with all updates installed.

---

### Post by ohnonot on 2013-05-23
i'm no linux god, but i'm pretty sure it's safe to delete log files.
yes, you should find out *why* it grew so large, but it might prove impossible to open a 9.8gb textfile...
delete it (no trash can!), reboot, see if you have your 9.8gb back, find the same file and see what it contains and if it grows again so large, maybe across a few reboots.
i hope the 1000+ beans agree with me on that...

---

### Post by azdavef on 2013-05-23
> **ohnonot said:**
> i'm no linux god, but i'm pretty sure it's safe to delete log files.
yes, you should find out *why* it grew so large, but it might prove impossible to open a 9.8gb textfile...
delete it (no trash can!), reboot, see if you have your 9.8gb back, find the same file and see what it contains and if it grows again so large, maybe across a few reboots.
i hope the 1000+ beans agree with me on that...

Thanks.  When I try to gksudo nautilus, I get "device is full error".  Is there another way to get at ot?

---

### Post by azdavef on 2013-05-23
> **azdavef said:**
> Thanks.  When I try to gksudo nautilus, I get "device is full error".  Is there another way to get at ot?

I got the same error with th rm command, but the shred command appears to have removed it.  I have most of my Root File System back and the lightdm.log reappeared after reboot with a much smaller size.  Thanks for you help, I hope to figure out what caused it.

---

### Post by HiImTye on 2013-05-23
clear some space first, and use something lightweight to read it, like 'less' as you'll need a lot of free mem to read it. you'll likely need to use the terminal (ctrl+alt+t)

---

### Post by ohnonot on 2013-05-24
you marked this as solved.
it would be good to let others know how you solved it.
that's what forums are for.

---

### Post by dasjefe on 2013-09-17
I'm having the same issue. My lightdm.log was >100GB when I deleted it. It is back and growing once again. I had the same problem with the .xsession-errors file. However, I was able to delete/recreate and set this file to immutable and that problem went away. I can't seem to use the same trick for the lightdm.log file. Does anyone have a solution for this besides just deleting it all the time? Thanks!

---

### Post by morrcahn on 2013-09-17
> **dasjefe said:**
> I'm having the same issue. My lightdm.log was >100GB when I deleted it. It is back and growing once again. I had the same problem with the .xsession-errors file. However, I was able to delete/recreate and set this file to immutable and that problem went away. I can't seem to use the same trick for the lightdm.log file. Does anyone have a solution for this besides just deleting it all the time? Thanks!

You could set up a cron job (sudo crontab -e) that would empty it every week or every two days-- however often you feel necessary.
```
0 3 */2 * * > /var/log/lightdm/lightdm.log # empty the file at 3AM every two days.
``` 
I would also look into the man page for crontab for examples (man 5 crontab). This doesn't figure out the reason for it becoming so large, but automates emptying the file.

---

### Post by VMC on 2013-09-17
To the OP, is this from when you first installed 12.04? Mine is only 2.3kb, but I re-install when more frequently. You can also 'head or tail' that file, but you must use root ```
 sudo  /var/log/lightdm/x-0.log or lightdm.log
```. This is the first time I ever looked at that log. No errors, just Initializing and DEBUG messages.

Maybe you have some errors in there, and that is why its filling up.

---

### Post by dasjefe on 2013-09-18
Thanks for the ideas. I might end up having to just setup a cron job. A little more info: This is a headless 13.04 system that I only access through SSH/VNC. This error appears to be related to vino. Here's a section of the lightdm.log file:

18/09/2013 09:17:10 AM Client Protocol Version 3.4  
 18/09/2013 09:17:10 AM Ignoring minor version mismatch  
 

 ** (vino-server:1799): WARNING **: Deferring authentication of 'mail.probldgsys$  
 

 

 ** (vino-server:1799): WARNING **: VNC authentication failure from 'emr.houston$  
 

 18/09/2013 09:17:11 AM rfbAuthPasswordChecked: password check failed  
 18/09/2013 09:17:11 AM [IPv4] Got connection from client emr.houstonrheum.com  
 18/09/2013 09:17:11 AM   other clients: 
 18/09/2013 09:17:11 AM      mail.probldgsystems.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      host.colocrossing.com  
 18/09/2013 09:17:11 AM      mailer.gonetwork.it  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      ks3001456.kimsufi.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      mail.probldgsystems.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      mail.probldgsystems.com  
 18/09/2013 09:17:11 AM      mail.probldgsystems.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      emr.houstonrheum.com  
 18/09/2013 09:17:11 AM      dasjefe-PC  
 18/09/2013 09:17:11 AM Client Protocol Version 3.4  
 18/09/2013 09:17:11 AM Ignoring minor version mismatch  
 

 ** (vino-server:1799): WARNING **: Deferring authentication of 'emr.houstonrheu$  
 

 

 ** (vino-server:1799): WARNING **: VNC authentication failure from 'mail.probld$  
 

 18/09/2013 09:17:16 AM rfbAuthPasswordChecked: password check failed  
 

 ** (vino-server:1799): WARNING **: VNC authentication failure from 'emr.houston$  
 

 18/09/2013 09:17:17 AM rfbAuthPasswordChecked: password check failed  
 8/09/2013 09:17:17 AM rfbAuthPasswordChecked: password check failed  
 18/09/2013 09:17:17 AM [IPv4] Got connection from client emr.houstonrheum.com  
 18/09/2013 09:17:17 AM   other clients:

---

