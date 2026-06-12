---
title: "Yahoo Messenger"
date: 2008-05-21
forum: General Help
---

### Post by mygravity on 2008-05-21
Hi all,

In the last few days Gaim hasn't been able to connect to the Yahoo Messenger service. It displays "<username> disconnnected: Unable to read" at the bottom of the Buddy List.

When trying to telnet to the required ports quite alot are refused connection:

20   - Connection refused
23   - Connection refused
25   - Connection refused
80   - OK
119  - Connection refused
5050 - OK
8001 - Connection refused
8002 - Connection refused

The refusal error looks like this:
telnet scs.msg.yahoo.com 20
Trying 216.155.193.132...
Trying 216.155.193.133...
Trying 216.155.193.134...
Trying 216.155.193.135...
Trying 216.155.193.128...
Trying 216.155.193.129...
Trying 216.155.193.130...
Trying 216.155.193.131...
telnet: Unable to connect to remote host: Connection refused

Has anyone experienced this? Any ideas for fixes?

Many thanks

Andrew


Required ports for Yahoo Messenger:
[http://help.yahoo.com/l/us/yahoo/messenger/messenger8/messenger/messenger-03.html](http://help.yahoo.com/l/us/yahoo/messenger/messenger8/messenger/messenger-03.html)

---

### Post by mygravity on 2008-05-28
Seems that as we can connect to port 5050 then we *should* be able to connect to Yahoo IM. Any ideas how to debug this problem?

Thanks

Andrew

---

