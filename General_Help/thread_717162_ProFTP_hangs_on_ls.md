---
title: "ProFTP hangs on ls"
date: 2008-03-06
forum: General Help
---

### Post by utahcon on 2008-03-06
I have some virtualhosts setup on my ProFTP, below is the conf:

```

ServerName                      "ProFTPD"
ServerType                      standalone
DefaultServer                   on

Port                            21
Umask                           022

MaxInstances                    30

User                            nobody
#Group                          nogroup

<Directory /opt/lampp/htdocs/*>
  AllowOverwrite                on
</Directory>

DefaultRoot /opt/lampp/htdocs

RequireValidShell off

UseFtpUsers off

#include /opt/lampp/etc/ftp.hosts/ftp.includes

#### DirectProDesign ####
<VirtualHost www.domain2.com ftp.domain2.com>
    DefaultRoot /opt/lampp/htdocs/domain2.com
    Port            4000
    AllowOverwrite  on
    <Limit LOGIN>
        AllowUser   user2
        DenyAll
    </Limit>
</VirtualHost>

#### FDDHosting.com ####
<VirtualHost www.domain1.com ftp.domain1.com>
    DefaultRoot     /opt/lampp/htdocs/domain1.com
    Port                 4001
    AllowOverwrite  on
    <Limit LOGIN>
        AllowUser   user1 user2
        DenyAll
    </Limit>
</VirtualHost>

```

As you can see I am using two different ports, 4000 and 4001.

When I do (from konsole):
```
ftp www.domain1.com 4000
```

I can login and do all things normal.

When I do 
```
ftp www.domain2.com 4001
```

I am authorized, as user 2, and then I try to ls and I get (shown from successful login)
```

230 User abarrett logged in
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful

```

Then it sits until my server disconnects (approx 20-30 seconds)

I cannot see any reason it wouldn't allow the user to login.

---

### Post by dcstar on 2008-03-07
> **utahcon said:**
> 
.........
I am authorized, as user 2, and then I try to ls and I get (shown from successful login)
```

230 User abarrett logged in
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful

```

Then it sits until my server disconnects (approx 20-30 seconds)

I cannot see any reason it wouldn't allow the user to login.

And these accounts have appropriate permissions on the directory you log them into?

---

