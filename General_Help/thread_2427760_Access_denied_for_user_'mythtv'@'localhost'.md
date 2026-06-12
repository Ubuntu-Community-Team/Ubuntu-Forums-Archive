---
title: "Access denied for user 'mythtv'@'localhost'"
date: 2019-09-25
forum: General Help
---

### Post by Denis_Papathanasio on 2019-09-25
I'm getting this error when mythbackend tries to start (I'm running the latest release of mythbuntu, 16.04).

I have already gone through all the steps here, without having found the problem:

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

The strange thing is, both ~/.mythtv/config.xml and /etc/mythtv/config.xml have the same Database block:

```
<Database>
    <PingHost>1</PingHost>
    <Host>localhost</Host>
    <UserName>mythtv</UserName>
    <Password>[elided]</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>

```

And when I try this, I *can* login successfully:

```
mysql -u mythtv mythconverg --password=[elided]
```

I also logged in to the mysql database as root, and confirmed the entries in the `user` table:

```
mysql> select host, user, authentication_string from user;
+-----------+------------------+-------------------------------------------+
| host      | user             | authentication_string                     |
+-----------+------------------+-------------------------------------------+
| localhost | root             | *71E7E31A1A32F0A0894FED209236F449DD44BE13 |
| localhost | mysql.sys        | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE |
| localhost | debian-sys-maint | *FB443C6A76C8438BEAC21A75DF59D68C2049DE88 |
| localhost | mythtv           | *E33BD981FCD6B8C6D5AA434E3ADC607A0B77FF8B |
| localhost | mysql.session    | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE |
+-----------+------------------+-------------------------------------------+

```

Sure enough, the `authentication_string` corresponding to the `mysql` user is equivalent to the mysql `PASSWORD()` function on the same string in both config.xml files.

So I'm at a loss to understand what the problem is... the user entries for `mysql.sys` and `mysql.session` seem suspicious b/c of their obviously wrong authentication string values, but that's not what the backend is using to login.

Any ideas what the problem is?

---

