---
title: "Port 3306 connection refused"
date: 2017-12-19
forum: General Help
---

### Post by timothylegg on 2017-12-19
Hello, I am running Ubuntu 16.04 as a virtual machine on a host system managed by another department.

 I want MariaDB to be remotely accessible on port 3306.

On the console, I can telnet localhost 3306 and see that I could hypothetically interact with the SQL server.

```
$ telnet localhost 3306
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
j
5.5.5-10.0.31-MariaDB-0ubuntu0.16.04.2Dquwtcq08-?f{X'U[F-Lv20mysql_native_password

```
On the same console, I can use the machine's IP address and I get "Connection refused".

```

$ telnet 10.204.x.y 3306
Trying 10.201.x.y...
telnet: Unable to connect to remote host: Connection refused

```

To the best of my knowledge the firewall is disabled, but I cannot  promise that there is only one firewall installed.  The network and  virtual machine admins tell me the packets are blocked within my  machine.  From this, I ask for two approaches to this.  How can I  either:

 
[LIST]
[*]Prove that my machine is listening on 3306?
[*]Determine the fault on my system?
[/LIST]
 
Being a virtual machine, I lack the convenience of carrying in my  Linksys SOHO router and plugging this machine and my laptop into it to  eliminate my machine as the source of the fault.  I only have a highly  awkward access to the host system admin panel (imagine a crowd of system  admins standing behind my shoulders and snooper-vising as I attempt to  tinker with VMWare on a Microsoft product).  I am open to using network  diagnosis tools, but lack expertise in their operation.

This problem may also be related to a separate issue that appeared last  week on Tuesday: outgoing port 80/443 requests also not working as of  Tuesday morning last week.

```
$ openssl s_client -connect google.com:443
connect: Connection refused
connect:errno=111
```

```
$ telnet www.google.com 80
Trying 172.217.21.100...
Trying 2a00:1450:4016:80a::2004...
telnet: Unable to connect to remote host: Network is unreachable
```

In fact the only port 80 addresses that I've verified to work are either localhost or the inet address 10.201.x.y...

Any ideas?

---

### Post by howefield on 2017-12-19
Duplicate thread closed.

---

