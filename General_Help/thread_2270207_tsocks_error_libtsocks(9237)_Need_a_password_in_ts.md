---
title: "tsocks error: libtsocks(9237): Need a password in tsocks.con"
date: 2015-03-21
forum: General Help
---

### Post by shamsat on 2015-03-21
when i run tsocks in ubuntu 14.10 get this error:
> 
14:35:05 libtsocks(9237): Need a password in tsocks.conf or $TSOCKS_PASSWORD to authenticate with14:35:05


My /etc/tsocks.conf  have only these lines enabled:
> 
local = 192.168.0.0/255.255.255.0
local = 10.0.0.0/255.0.0.0
# Default server
server = 127.0.0.1
server_type = 5
server_port = 9050


---

### Post by dino99 on 2015-03-21
yes it needs to be set:
 [http://manpages.ubuntu.com/manpages/utopic/man5/tsocks.conf.5.html](http://manpages.ubuntu.com/manpages/utopic/man5/tsocks.conf.5.html)
[http://www.binarytides.com/proxify-applications-with-tsocks-and-proxychains-on-ubuntu/](http://www.binarytides.com/proxify-applications-with-tsocks-and-proxychains-on-ubuntu/)

---

