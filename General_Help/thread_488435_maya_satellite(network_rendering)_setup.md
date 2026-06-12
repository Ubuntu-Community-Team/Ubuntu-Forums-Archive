---
title: "maya satellite(network rendering) setup"
date: 2007-06-30
forum: General Help
---

### Post by tempo500 on 2007-06-30
could someone enlighten me on how to start a process, or how to check if it is running. maybee someone can translate this fedora instruction?... thanks, phil

```
on Linux (SuSE, RedHat, and Fedora Core) xinetd services can be
monitored using the chicaning command-line utility. For example:

    /sbin/chkconfig -list mi-raysat85

This should report mi-raysat85 as an "xinetd based service" and
state whether it is on or off.

If the xinetd service is not installed it will report "unknown
service". If you get this message ensure that mr Satellite RPM
is installed (the default install location is /usr/autodesk/mentalraysat85/).

If the software is installed, but not showing up with the above
"-list" command, the service can be added using the
netsetup_satellite utility:

    /usr/autodesk/mentalraysat85/bin/netsetup_satellite

If the service is showing up but is not on, it can be activated
as follows:

    /sbin/chkconfig -set mi-raysat85 on
```
```
Slave machine port setup
------------------------

Port number 7106 is set by default. To change the port number
used by mental ray satellite, you must edit the services file.

To change the port number

1. Edit the services file.

   The services file is located at:

   (Linux) /etc/services

2. Change the number in the following line (here, 7106) to the
desired port number:

   mi-raysat85   7106/tcp

3. Restart the server.

   * (Linux [SuSE, RedHat, and Fedora Core] - Advanced), The xinetd 
     service can be re-started using the chicaning utility (as a root user):

    /sbin/chkconfig -set xinetd off
    /sbin/chkconfig -set xinetd on

   This will stop, then restart the xinetd process, forcing it to
   reload settings such as port numbers.
```

---

