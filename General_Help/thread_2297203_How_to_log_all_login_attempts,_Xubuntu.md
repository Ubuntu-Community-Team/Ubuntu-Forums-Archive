---
title: "How to log all login attempts, Xubuntu"
date: 2015-10-01
forum: General Help
---

### Post by Ralph L on 2015-10-01
I am running xubuntu 14.04LTS.  To access my computer I just login from the keyboard with my admin name and password.  I don't run any web server.  I read various web sites saying to pay attention to security and that I should log all attempted logins.  How do I do this??  Also, this web site refers to SSH ([https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) ).  It gives some warnings about disabling SSH.  I have never installed or activated SSH.  Is there anything I should do to disable it???  

One more question:  I store most of my passwords using the "Remember Password" window that pops up, when I enter a password.  Is this secure???

Thanks for any help....

---

### Post by TheFu on 2015-10-01
a) don't use web browser password stores for anything you care about.
b) running an ssh server can be extremely helpful, and if secured properly (easy), doesn't cause any extra security concern for a home user.  After all, if the PC is upstairs and you are downstairs with a netbook/tablet, wouldn't it be nice to ssh in and do some simple maintenance?  BTW - upstairs/downstairs could be London/Kathmandu just as easily. ssh is extremely useful, even for non-power-users.
c) Attempted logins ARE logged.  The log files are in /var/log.  Depending on how the login attempt is made, it will be in a different log file.  For a home user, running zero services (like ssh), the "auth.log" is it.

* Secure SSH [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
* What can SSH do?  [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

For most people who choose to run Linux, sftp is worth the price to have secure, remote access to their files. Basically every OS with networking has a great sftp client.

---

### Post by Ralph L on 2015-10-02
TheFu,
Thanks for responding.  You gave me some useful information.  I looked at the file /var/log/auth.log.  It has lots of entries--most of which I don't understand.  Are there any entries that I should grep for that would hint at somebody hacking my system?

---

