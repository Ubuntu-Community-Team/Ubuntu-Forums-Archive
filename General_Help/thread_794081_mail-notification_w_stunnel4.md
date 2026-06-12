---
title: "mail-notification w/ stunnel4"
date: 2008-05-14
forum: General Help
---

### Post by trmentry on 2008-05-14
I realize that mail-notification doesn't have SSL support built in, but using stunnel as a work around works well.  But I seem to have an odd issue.

I have mail-notification setup to start on session start.  The little box ticked in the config.  Stunnel starts up on boot as well.  Running Hardy 32bit.

Anyway.. the issue I have is when I logon my session, mail-notification will show that it can't connect.  

I restart Stunnel4 and try again, and its fine.  

My stunnel.conf is fairly stock.   Just have  
client = yes

[imap]
accept = 1143
connect = imap.gmail.com:993

This is for Google Apps as it appears mail-notification doesn't support Google Apps with the Gmail option.

Anyway... I'm confused as to why this is happening and can't find any reason for it.

Has anyone else seen this or can point me in the right direction?

Thanks

---

### Post by trmentry on 2008-05-16
Anyone?

---

### Post by trmentry on 2008-05-20
This appears to be a Stunnel issue.  When I first boot up the machine, I Stunnel won't accept the connections.  But if I restart it, its fine.

I tried to change the listen (accept) port to something below 1024 thinking maybe that was the issue.  Apparently not.

```

$ telnet localhost 143
Trying 127.0.0.1...
Connected to localhost.
telnet: Unable to connect to remote host: connection reset by peer.
$
$ sudo /etc/init.d/stunnel4 restart
[sudo] password for trmentry:
Restarting SSL tunnels: [stopped: /etc/stunnel/stunnel.conf] [Started: /etc/stunnel/stunnel.conf] stunnel.
$
$ telnet localhost 143
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK Gimap ready for requests from 70.228.53.2 w43if15712pyg.0

```

---

