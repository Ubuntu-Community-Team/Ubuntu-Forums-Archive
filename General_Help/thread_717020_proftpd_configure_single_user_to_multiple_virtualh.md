---
title: "proftpd configure single user to multiple virtualhosts"
date: 2008-03-06
forum: General Help
---

### Post by utahcon on 2008-03-06
I am trying to configure proftpd for some virtualhosts. 

It is accepting connections and logins, however it is chrooting my users to the first VirtualHost they are found under. Here is my example

```

#### Domain1 ####
<VirtualHost www.domain1.com ftp.domain1.com>
    DefaultRoot /opt/lampp/htdocs/domain1.com
    AllowOverwrite  on
    <Limit LOGIN>
        AllowUser   joeuser1
        DenyAll
    </Limit>
</VirtualHost>

#### Domain2 ####
<VirtualHost www.domain2.com ftp.domain2.com>
    DefaultRoot /opt/lampp/htdocs/domain2.com
    AllowOverwrite  on
    <Limit LOGIN>
        AllowUser   joeuser1
        DenyAll
    </Limit>
</VirtualHost>

```

When joeuser1 logs into domain2 he is chroot to domain1

Here is the rest of my conf
```

ServerName          "ProFTPD"
ServerType          standalone
DefaultServer           on
Port                21
Umask               022
MaxInstances            30
User                nobody
#Group              nogroup
<Directory /opt/lampp/htdocs/*>
  AllowOverwrite        on
</Directory>
DefaultRoot /opt/lampp/htdocs
RequireValidShell off
UseFtpUsers off

```

---

