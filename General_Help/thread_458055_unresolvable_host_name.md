---
title: "unresolvable host name"
date: 2007-05-29
forum: General Help
---

### Post by vortmax on 2007-05-29
I'm hitting a strange problem my fiesty server.  I am running both samba and apache.

From my computer running XP-pro, I can access the samba shares with '\\mediaserver' and the http home page with [http://mediaserver](http://mediaserver).  Everything works without a hitch.

My wife's computer running xp home is another story.  it is configured to the correct workgroup and everything.  It cannot resolve the server at all.  If you attempt to ping the server name, it can't find it. However if you nbtstat the IP you get:

```


Wireless Network Connection:
Node IpAddress: [192.***.***.***] Scope Id: []

           NetBIOS Remote Machine Name Table

       Name               Type         Status
    ---------------------------------------------
    MEDIASERVER    <00>  UNIQUE      Registered
    MEDIASERVER    <03>  UNIQUE      Registered
    MEDIASERVER    <20>  UNIQUE      Registered
    ..__MSBROWSE__.<01>  GROUP       Registered
    SKYNET         <1D>  UNIQUE      Registered
    SKYNET         <1E>  GROUP       Registered
    SKYNET         <00>  GROUP       Registered

    MAC Address = 00-00-00-00-00-00

```

note:  I ***'d out the ip address.

So the xp-home computer can see the server (it's not being blocked), but can't resolve it by host name.  Both the XP-home and pro computers are accessing the server via wireless through the same router.

Thoughts?

Is this an issue with the server config or the computer?

---

### Post by sanoj on 2007-05-29
Just a thought: How is hostname mapped to IP? I know nothing about XP or samba, but it seems like a question you might want to answer.

EDIT: I am not familiar with "nbstat", but I think it might be another protocol than IP, in which case the fact that it can be "seen" does not apply to programs using IP protocols (which samba probably does).

---

