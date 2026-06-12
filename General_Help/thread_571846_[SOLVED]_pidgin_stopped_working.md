---
title: "[SOLVED] pidgin stopped working"
date: 2007-10-09
forum: General Help
---

### Post by billybag on 2007-10-09
For some reason when i started up m,y computer and started pidgin... it logs on and then freezes. i have tried removing and reinstalling it and still the same thing... any ideas?

okay and it seems ubuntu also freezes a little later on... some times

---

### Post by billybag on 2007-10-09
anyone? please?

ive tried reverting back to older versions and that doesnt work either.

it starts up. works fine for about 5 seconds. then freezes. what is up?

is their anything i can post that would help...? kind of sucks... even just an idea may be nice

---

### Post by billybag on 2007-10-09
OKAY OKAY so i got it to work when i run it through terminal.

im going to see if restarting my computer helps i guess.

nope that didnt work.

so again. it works in terminal. but it doesnt work regularly. it works for about 5 or 10 seconds then just freezes.

---

### Post by billybag on 2007-10-09
do you think it would be fixed if i upgraded to Gutsy? reinstalling gnome perhaps?

..........

is their a way i can some how log/record what is going on into terminal or a document? gr this is so annoying.

---

### Post by billybag on 2007-10-10
very very hard to do, but i managed to copy and paste the debug window info before the freeze:
```

(18:45:47) account: Connecting to account SCREENNAME
(18:45:47) util: Writing file prefs.xml to directory /home/billy/.purple
(18:45:47) util: Writing file /home/billy/.purple/prefs.xml
(18:45:47) util: Writing file accounts.xml to directory /home/billy/.purple
(18:45:47) util: Writing file /home/billy/.purple/accounts.xml
(18:45:47) util: Writing file blist.xml to directory /home/billy/.purple
(18:45:47) util: Writing file /home/billy/.purple/blist.xml
(18:45:47) dns: Created new DNS child 8698, there are now 1 children.
(18:45:47) dns: Successfully sent DNS request to child 8698
(18:45:47) Session Management: Received first save_yourself
(18:45:47) Session Management: Received save_complete
(18:45:47) util: requested to fetch (http://192.168.0.1:5678/igd.xml), full=1, user_agent=((null)), http11=1
(18:45:47) dns: DNS query for '192.168.0.1' queued
(18:45:47) dns: Created new DNS child 8700, there are now 2 children.
(18:45:47) dns: Successfully sent DNS request to child 8700
(18:45:47) dns: Got response for '192.168.0.1'
(18:45:47) dnsquery: IP resolved for 192.168.0.1
(18:45:47) proxy: Attempting connection to 192.168.0.1
(18:45:47) proxy: Connecting to 192.168.0.1:5678 with no proxy
(18:45:47) proxy: Connection in progress
(18:45:47) proxy: Connected to 192.168.0.1:5678.
(18:45:47) util: Request: 'GET /igd.xml HTTP/1.1

Connection: close

Host: 192.168.0.1:5678



'
(18:45:48) docklet: embedded
(18:45:48) dns: Got response for 'currenttrack.sf.net'
(18:45:48) dnsquery: IP resolved for currenttrack.sf.net
(18:45:48) proxy: Attempting connection to 66.35.250.209
(18:45:48) proxy: Connecting to currenttrack.sf.net:80 with no proxy
(18:45:48) proxy: Connection in progress
(18:45:48) util: Response headers: 'HTTP/1.1 200 OK

Server: Embedded HTTP Server 1.00

Content-Type: text/xml

Content-Length: 2881

Connection: close



'
(18:45:48) util: parsed 2881
(18:45:48) upnp: parse_description_response(): could not get serviceTypeNode 7
(18:45:48) upnp: purple_upnp_parse_description(): control URL is NULL
(18:45:48) proxy: Connected to currenttrack.sf.net:80.
(18:45:48) util: Request: 'GET /update/update.ini HTTP/1.1

Connection: close

User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.1) Gecko/20060111 Firefox/1.5.0.1

Accept: */*

Host: currenttrack.sf.net



'
(18:45:48) network: Entering nm_callback_func!
(18:45:48) autorecon: do_signon called
(18:45:48) autorecon: calling purple_account_connect
(18:45:48) account: Connecting to account winkyfletcher
(18:45:49) autorecon: done calling purple_account_connect
(18:45:49) util: Writing file pounces.xml to directory /home/billy/.purple
(18:45:49) util: Writing file /home/billy/.purple/pounces.xml
(18:45:49) util: Response headers: 'HTTP/1.1 302 Found

Date: Wed, 10 Oct 2007 22:45:48 GMT

Server: Apache/1.3.33 (Unix) PHP/4.3.10

Location: http://currenttrack.sourceforge.net/update/update.ini

Connection: close

Transfer-Encoding: chunked

Content-Type: text/html; charset=iso-8859-1

X-Pad: avoid browser bug



'
(18:45:49) util: Redirecting to http://currenttrack.sourceforge.net/update/update.ini
(18:45:50) dns: DNS query for 'currenttrack.sourceforge.net' queued
(18:45:50) dns: Created new DNS child 8702, there are now 1 children.
(18:45:50) dns: Successfully sent DNS request to child 8702
(18:45:50) dns: Got response for 'currenttrack.sourceforge.net'
(18:45:50) dnsquery: IP resolved for currenttrack.sourceforge.net
(18:45:50) proxy: Attempting connection to 66.35.250.209
(18:45:50) proxy: Connecting to currenttrack.sourceforge.net:80 with no proxy
(18:45:50) proxy: Connection in progress
(18:45:50) proxy: Connected to currenttrack.sourceforge.net:80.
(18:45:50) util: Request: 'GET /update/update.ini HTTP/1.1

Connection: close

User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.1) Gecko/20060111 Firefox/1.5.0.1

Accept: */*

Host: currenttrack.sourceforge.net



'
(18:45:50) util: Response headers: 'HTTP/1.1 200 OK

Date: Wed, 10 Oct 2007 22:45:50 GMT

Server: Apache/1.3.33 (Unix) PHP/4.3.10

Last-Modified: Tue, 22 May 2007 07:31:54 GMT

ETag: "35393f6-7f-46529c6a"

Accept-Ranges: bytes

Content-Length: 127

Connection: close

Content-Type: text/plain



'
(18:45:50) util: parsed 127
```

and when i use pidgin through root terminal command, pidgin works fine so here is the debug window info for that:

```


(18:51:26) account: Connecting to account SCREENAME
(18:51:26) connection: Connecting. gc = 0x85b6a38
(18:51:26) oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
(18:51:26) oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
(18:51:26) oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
(18:51:26) oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
(18:51:26) oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
(18:51:26) oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
(18:51:26) oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
(18:51:26) oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
(18:51:26) oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
(18:51:26) oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
(18:51:26) oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
(18:51:26) oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
(18:51:26) oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
(18:51:26) oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
(18:51:26) oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
(18:51:26) oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
(18:51:26) oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
(18:51:26) oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
(18:51:26) oscar: Adding handler for ffff/0003
(18:51:26) oscar: Adding handler for ffff/0006
(18:51:26) oscar: Adding handler for 0007/0003
(18:51:26) oscar: Adding handler for 0007/0005
(18:51:26) oscar: Adding handler for 0007/0007
(18:51:26) oscar: Adding handler for 0018/0001
(18:51:26) oscar: Adding handler for 0018/0007
(18:51:26) oscar: Adding handler for 0017/0003
(18:51:26) oscar: Adding handler for 0017/0007
(18:51:26) oscar: Adding handler for 0017/000a
(18:51:26) oscar: Adding handler for 0010/0005
(18:51:26) oscar: Adding handler for 0009/0001
(18:51:26) oscar: Adding handler for 0009/0003
(18:51:26) oscar: Adding handler for 0003/0001
(18:51:26) oscar: Adding handler for 0003/0003
(18:51:26) oscar: Adding handler for 0003/000b
(18:51:26) oscar: Adding handler for 0003/000c
(18:51:26) oscar: Adding handler for 000e/0001
(18:51:26) oscar: Adding handler for 000e/0003
(18:51:26) oscar: Adding handler for 000e/0004
(18:51:26) oscar: Adding handler for 000e/0002
(18:51:26) oscar: Adding handler for 000e/0006
(18:51:26) oscar: Adding handler for 000d/0001
(18:51:26) oscar: Adding handler for 000d/0009
(18:51:26) oscar: Adding handler for 0013/0001
(18:51:26) oscar: Adding handler for 0013/0003
(18:51:26) oscar: Adding handler for 0013/0006
(18:51:26) oscar: Adding handler for 0013/000e
(18:51:26) oscar: Adding handler for 0013/0008
(18:51:26) oscar: Adding handler for 0013/0009
(18:51:26) oscar: Adding handler for 0013/0015
(18:51:26) oscar: Adding handler for 0013/0019
(18:51:26) oscar: Adding handler for 0013/001b
(18:51:26) oscar: Adding handler for 0013/001c
(18:51:26) oscar: Adding handler for 0004/0005
(18:51:26) oscar: Adding handler for 0004/0007
(18:51:26) oscar: Adding handler for 0004/000a
(18:51:26) oscar: Adding handler for 0004/000b
(18:51:26) oscar: Adding handler for 0004/0001
(18:51:26) oscar: Adding handler for 0004/0014
(18:51:26) oscar: Adding handler for 0004/000c
(18:51:26) oscar: Adding handler for 0015/00f0
(18:51:26) oscar: Adding handler for 0015/00f1
(18:51:26) oscar: Adding handler for 0015/00f3
(18:51:26) oscar: Adding handler for 0015/00f2
(18:51:26) oscar: Adding handler for 0002/0003
(18:51:26) oscar: Adding handler for 0002/0006
(18:51:26) oscar: Adding handler for 0002/0001
(18:51:26) oscar: Adding handler for 0002/fffd
(18:51:26) oscar: Adding handler for 0001/0001
(18:51:26) oscar: Adding handler for 0001/000f
(18:51:26) oscar: Adding handler for 0001/001f
(18:51:26) oscar: Adding handler for 0001/0021
(18:51:26) oscar: Adding handler for 0001/000a
(18:51:26) oscar: Adding handler for 0001/0005
(18:51:26) oscar: Adding handler for 0001/0013
(18:51:26) oscar: Adding handler for 0001/0010
(18:51:26) oscar: Adding handler for 0008/0002
(18:51:26) oscar: Adding handler for 000a/0001
(18:51:26) oscar: Adding handler for 000a/0003
(18:51:26) oscar: oscar_login: gc = 0x85b6a38
(18:51:26) dns: DNS query for 'login.messaging.aol.com' queued
(18:51:26) dns: Created new DNS child 8978, there are now 1 children.
(18:51:26) dns: Successfully sent DNS request to child 8978
(18:51:26) dns: Created new DNS child 8979, there are now 2 children.
(18:51:26) dns: Successfully sent DNS request to child 8979
(18:51:26) util: requested to fetch (http://192.168.0.1:5678/igd.xml), full=1, user_agent=((null)), http11=1
(18:51:26) dns: DNS query for '192.168.0.1' queued
(18:51:26) dns: Got response for 'currenttrack.sf.net'
(18:51:26) dnsquery: IP resolved for currenttrack.sf.net
(18:51:26) proxy: Attempting connection to 66.35.250.209
(18:51:26) proxy: Connecting to currenttrack.sf.net:80 with no proxy
(18:51:26) proxy: Connection in progress
(18:51:26) dns: Created new DNS child 8981, there are now 2 children.
(18:51:26) dns: Successfully sent DNS request to child 8981
(18:51:27) dns: Got response for 'login.messaging.aol.com'
(18:51:27) dnsquery: IP resolved for login.messaging.aol.com
(18:51:27) proxy: Attempting connection to 64.12.161.153
(18:51:27) proxy: Connecting to login.messaging.aol.com:5190 with no proxy
(18:51:27) proxy: Connection in progress
(18:51:27) dns: Got response for '192.168.0.1'
(18:51:27) dnsquery: IP resolved for 192.168.0.1
(18:51:27) proxy: Attempting connection to 192.168.0.1
(18:51:27) proxy: Connecting to 192.168.0.1:5678 with no proxy
(18:51:27) proxy: Connection in progress
(18:51:27) proxy: Connected to 192.168.0.1:5678.
(18:51:27) util: Request: 'GET /igd.xml HTTP/1.1

Connection: close

Host: 192.168.0.1:5678



'
(18:51:27) proxy: Connected to login.messaging.aol.com:5190.
(18:51:27) oscar: connected to FLAP server of type 0x0017
(18:51:27) oscar: Screen name sent, waiting for response
(18:51:27) proxy: Connected to currenttrack.sf.net:80.
(18:51:27) util: Request: 'GET /update/update.ini HTTP/1.1

Connection: close

User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.1) Gecko/20060111 Firefox/1.5.0.1

Accept: */*

Host: currenttrack.sf.net



'
(18:51:27) docklet: embedded
(18:51:27) util: Response headers: 'HTTP/1.1 302 Found

Date: Wed, 10 Oct 2007 22:51:27 GMT

Server: Apache/1.3.33 (Unix) PHP/4.3.10

Location: http://currenttrack.sourceforge.net/update/update.ini

Connection: close

Transfer-Encoding: chunked

Content-Type: text/html; charset=iso-8859-1

X-Pad: avoid browser bug



'
(18:51:27) util: Redirecting to http://currenttrack.sourceforge.net/update/update.ini
(18:51:27) dns: DNS query for 'currenttrack.sourceforge.net' queued
(18:51:27) oscar: inside auth_resp (Screen name: SCREENAME)
(18:51:27) oscar: Reg status: 3
(18:51:27) oscar: E-mail: dpshfbfb@hotmail.com
(18:51:27) oscar: BOSIP: 64.12.25.56:5190
(18:51:27) oscar: Closing auth connection...
(18:51:27) oscar: Scheduling destruction of FLAP connection of type 0x0017
(18:51:27) dns: DNS query for '64.12.25.56' queued
(18:51:27) dns: Created new DNS child 8984, there are now 1 children.
(18:51:27) dns: Successfully sent DNS request to child 8984
(18:51:27) oscar: Destroying oscar connection of type 0x0017.  Disconnect reason is 0
(18:51:27) oscar: Disconnected.  Code is 0x0000 and msg is 
(18:51:27) dns: Created new DNS child 8985, there are now 2 children.
(18:51:27) dns: Successfully sent DNS request to child 8985
(18:51:27) dns: Got response for '64.12.25.56'
(18:51:27) dnsquery: IP resolved for 64.12.25.56
(18:51:27) proxy: Attempting connection to 64.12.25.56
(18:51:27) proxy: Connecting to 64.12.25.56:5190 with no proxy
(18:51:27) proxy: Connection in progress
(18:51:27) proxy: Connected to 64.12.25.56:5190.
(18:51:27) oscar: connected to FLAP server of type 0x0002
(18:51:27) dns: Got response for 'currenttrack.sourceforge.net'
(18:51:27) dnsquery: IP resolved for currenttrack.sourceforge.net
(18:51:27) proxy: Attempting connection to 66.35.250.209
(18:51:27) proxy: Connecting to currenttrack.sourceforge.net:80 with no proxy
(18:51:27) proxy: Connection in progress
(18:51:27) oscar: MOTD: Unknown (5)
(18:51:27) network: Entering nm_callback_func!
(18:51:28) util: Writing file prefs.xml to directory /root/.purple
(18:51:28) util: Writing file /root/.purple/prefs.xml
(18:51:28) util: Writing file accounts.xml to directory /root/.purple
(18:51:28) util: Writing file /root/.purple/accounts.xml
(18:51:28) util: Writing file blist.xml to directory /root/.purple
(18:51:28) util: Writing file /root/.purple/blist.xml
(18:51:28) util: Response headers: 'HTTP/1.1 200 OK

Server: Embedded HTTP Server 1.00

Content-Type: text/xml

Content-Length: 2881

Connection: close



'
(18:51:28) util: parsed 2881
(18:51:28) upnp: parse_description_response(): could not get serviceTypeNode 7
(18:51:28) upnp: purple_upnp_parse_description(): control URL is NULL
(18:51:28) oscar: FLAP connection of type 0x0002 is now fully connected
(18:51:28) oscar: ssi: requesting rights and list
(18:51:28) proxy: Connected to currenttrack.sourceforge.net:80.
(18:51:28) util: Request: 'GET /update/update.ini HTTP/1.1

Connection: close

User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.1) Gecko/20060111 Firefox/1.5.0.1

Accept: */*

Host: currenttrack.sourceforge.net



'
(18:51:28) oscar: locate rights: max sig len = 4096
(18:51:28) oscar: buddy list rights: Max buddies = 1000 / Max watchers = 2000
(18:51:28) oscar: BOS rights: Max permit = 1000 / Max deny = 1000
(18:51:28) connection: Activating keepalive.
(18:51:28) oscar: buddy list loaded
(18:51:28) oscar: ssi rights:(18:51:28)  max type 0x0000=3000,(18:51:28)  max type 0x0001=61,(18:51:28)  max type 0x0002=1000,(18:51:28)  max type 0x0003=1000,(18:51:28)  max type 0x0004=1,(18:51:28)  max type 0x0005=1,(18:51:28)  max type 0x0006=150,(18:51:28)  max type 0x0007=12,(18:51:28)  max type 0x0008=12,(18:51:28)  max type 0x0009=3,(18:51:28)  max type 0x000a=50,(18:51:28)  max type 0x000b=50,(18:51:28)  max type 0x000c=0,(18:51:28)  max type 0x000d=0,(18:51:28)  max type 0x000e=0,(18:51:28)  max type 0x000f=0,(18:51:28)  max type 0x0010=0,(18:51:28)  max type 0x0011=1,(18:51:28)  max type 0x0012=0,(18:51:28)  max type 0x0013=0,(18:51:28)  max type 0x0014=15,(18:51:28)  max type 0x0015=1,(18:51:28)  max type 0x0016=40,(18:51:28)  max type 0x0017=1,(18:51:28)  max type 0x0018=10,(18:51:28)  max type 0x0019=200,(18:51:28)  max type 0x001a=1,(18:51:28)  max type 0x001b=0,(18:51:28)  max type 0x001c=200,(18:51:28)  max type 0x001d=1,(18:51:28)  max type 0x001e=8,(18:51:28)  max type 0x001f=20,(18:51:28)  max type 0x0020=0,(18:51:28)  max type 0x0021=10000,(18:51:28)  max type 0x0022=1000,(18:51:28)  max type 0x0023=1000,(18:51:28)  max type 0x0024=0,(18:51:28) 
(18:51:28) oscar: ssi: syncing local list and server list
(18:51:28) oscar: ssi: activating server-stored buddy list
(18:51:28) util: Response headers: 'HTTP/1.1 200 OK

Date: Wed, 10 Oct 2007 22:51:28 GMT

Server: Apache/1.3.33 (Unix) PHP/4.3.10

Last-Modified: Tue, 22 May 2007 07:31:54 GMT

ETag: "35393f6-7f-46529c6a"

Accept-Ranges: bytes

Content-Length: 127

Connection: close

Content-Type: text/plain



'
(18:51:28) util: parsed 127
(18:51:28) blist: Updating buddy status for SCREENAME (AIM)
```

---

