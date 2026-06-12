---
title: "Samba and nfs install problem"
date: 2007-11-09
forum: General Help
---

### Post by raydar on 2007-11-09
I just tried installing samba and nfs and got the error below.  I had vmware running, and Firefox and Thunderbird, but that's all.  Any ideas?

- - - - - - - - - IMPORTANT INFORMATION FOR XINETD USERS - - - - - - - - - -
The following line will be added to your /etc/inetd/conf file:

#<off># netbios-ssn	stream  tcp	nowait  root	/usr/sbin/tcpd /usr/sbin . . . .

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

  * Starting Samba daemons
    . . .done.

Processing triggers for libc6 . . .
ldconfig deferred processing now taking place
dpkg: subprocess post-installation script killed by signal (Interrupt)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up libc6 (2.6.1-1ubuntu10) . . .

Processing triggers for libc6 . . .
ldconfig deferred processing now taking place

---

