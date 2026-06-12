---
title: "Samba( Error returning browse list: NT_STATUS_OK )"
date: 2005-08-17
forum: General Help
---

### Post by Gefion on 2005-08-17
I had decided to move my post to the Hoary forum since i use Hoary and put it into Other Application Support.


[QUOTE=istoyanov]I have Linux box with Samba on a mixed (Linux and Windows boxes) network enviroment.
Windows boxes can browse and access all Linux shares. Linux boxes can browse only Win95/98 shares. When I try to obtain a list of shares on Win2000/XP machines using smbclient -L (without user name and password!!!)

I get: "Error returning browse list: NT_STATUS_ACCESS_DENIED"

The same command works fine for Win95/98 -- it shows all theirs shared resources.

Does anyone know what could be the problem?

Thank you in advance![/QUOTE]
 As for fixing the:
Error returning browse list: NT_STATUS_ACCESS_DENIED
you have to specify a valid XP user account when you do a smbclient -L HOST..

eg ( smbclient -L XPMACHINE -U user%password -N )

but that leads to my problem below....

I've been having the same problem...
I have samba setup with all the proper configuration options
(will display configuration on request)
when i attempt to obtain the XP computers share list i get

Error returning browse list: NT_STATUS_OK

below is the terminal input/output

```

foo@bar:~$ smbclient -L XPMACHINE -I 192.168.1.100 -U user%password -N
Domain=[XPMACHINE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_OK
Domain=[XPMACHINE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
foo@bar:~$

```

Also, I can access the XPShares via the use of smbmount/mount -t smbfs by specifying the share name i wish to use

```
 mount -t smbfs -o username=foo,password=bar //XPMACHINE/SHARE /mnt/point
```

so actually accessing the XP Shares is not a problem it's just retrieving a list of the XP Shares that is...

I've googled for a resolution to this error i believe it isn't a samba configuration problem but more so a XP problem. Anyone with suggestions on resolving this problem would be greatly appreciated.

---

### Post by nad on 2005-08-19
I'm not certain that you can use both th U and N arguments together. Try it with just a valid usename.

---

