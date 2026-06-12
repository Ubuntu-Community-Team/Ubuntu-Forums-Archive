---
title: "Ubuntu vsftpd trouble"
date: 2015-04-22
forum: General Help
---

### Post by ab0mber2015 on 2015-04-22
I have set up three virtualbox VMs in order to monitor traffic between two on a third, and I am having trouble with logging into ftp. This is all on a host only network.

When I enter the command 'ftp 192.xxx.xx.xxx' to connect via ftp to my other VM, it asks for a username and password. I have looked up several different ways to find or alter the username and password, but I have had no luck so far. What do I need to do to initiate an ftp sessions between these two VMs?

I apologize if the Ubuntu forums were not the proper place for this question, but I am at wit's end trying to figure this out. :mad: Any help anyone can offer would be appreciated.

---

### Post by bashiergui on 2015-04-26
To change the usernames and passwords use this
[http://serverfault.com/questions/511381/how-to-change-the-password-of-a-vsftpd-ftp-account-when-passwd-isnt-working](http://serverfault.com/questions/511381/how-to-change-the-password-of-a-vsftpd-ftp-account-when-passwd-isnt-working)

You can login using the credentials of whatever user is logged into the target machine. For instance, if Tom ftp's to Harry's computer, Tom can use Harry's credentials. If this is all host-only then you know all the credentials.

---

