---
title: "Firehol vs. Gaim"
date: 2007-01-19
forum: General Help
---

### Post by @ndy25 on 2007-01-19
Hi everybody,
i have a problem with configuration firehol. If firehol runs i cannot connect to Jabber protocol with Gaim.](*,) 
Here is my firehol.conf

```

#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

# Accept all client traffic on any interface
# interface any world
# client all accept

DEFAULT_CLIENT_PORTS="1024:65535"

server_icq_ports="tcp/5190"
client_icq_ports="default"
server_jabber_ports="tcp/5222 , tcp/5223"
client_jabber_ports="default"

interface ppp0 internet src not "${UNROUTABLE_IPS}"
    policy drop
    protection strong 10/sec 10
    server ident reject with tcp-reset
#    server ssh    accept
#    server ping    accept
    client dhcp    accept
    client dns      accept
    client http     accept
    client https    accept
    client ftp      accept
    client ntp      accept
    client ssh      accept
    client icq      accept
    client jabber accept
    client cups    accept
    client samba    accept

UNMATCHED_INPUT_POLICY="DROP"
UNMATCHED_OUTPUT_POLICY="DROP"
FIREHOL_LOG_LEVEL=4

```

When I restarted firehol with this configuration, there are these errors:
```

FireHOL: Processing file /etc/firehol/firehol.conf:
--------------------------------------------------------------------------------ERROR #: 1
WHAT   : Running simple rules for  client 'jabber'
WHY    : Cannot accept an empty 'dport'.
COMMAND: client jabber accept
SOURCE : line 40 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------ERROR #: 2
WHAT   : Running simple rules for  client 'jabber'
WHY    : Simple service 'jabber' returned an error (1).
COMMAND: client jabber accept
SOURCE : line 40 of /etc/firehol/firehol.conf


NOTICE: No changes made to your firewall.
 FAILED


FireHOL: Restoring old firewall: OK

```
Any Idea, how to right configure firehol?
Thanks a lot for your advance.;)

---

