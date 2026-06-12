---
title: "Samba doesn't work until after smbtree command executed"
date: 2019-05-07
forum: General Help
---

### Post by spivver on 2019-05-07
Hello,

I've got an Ubuntu 19.04 server.  Pretty basic.  It's joined to Active Directory.

I have configured a Samba share.  If I restart the smbd service after making any changes to smbd.conf:

```
sudo systemctl restart smbd
```

The server refuses connections:

```
smbclient -L servername
Unable to initialize messaging context
do_connect: Connection to servername failed (Error NT_STATUS_CONNECTION_REFUSED)

```

However if I run

```
sudo smbtree -d3
```

and authenticate with my AD password, I can then run the smbclient command, I'm asked to authenticate with my password (AD account), and then I can access SMB shares.

```
smbclient -L servername
Unable to initialize messaging context
Enter username@DOMAIN.LOCAL's password:


        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        share           Disk
        IPC$            IPC       IPC Service (servername server (Samba, Ubuntu))
Reconnecting with SMB1 for workgroup listing.


        Server               Comment
        ---------            -------


        Workgroup            Master
        ---------            -------
        DOMAIN        SERVERNAME

```

Any ideas?

---

