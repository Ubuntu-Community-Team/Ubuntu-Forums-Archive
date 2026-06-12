---
title: "help me: ACL configuration trouble with SQUID"
date: 2007-12-13
forum: General Help
---

### Post by mozkill on 2007-12-13
[COLOR="Red"]In my squid configuration file I have:[/COLOR]

acl home src 192.168.0.0/24
http_access allow home localhost

[COLOR="Red"]I also tried:[/COLOR]

acl home src 192.168.0.3
http_access allow home localhost
[COLOR="Red"]
But it wont work.  The only way I can get squid to work is by:[/COLOR]

acl all src 0.0.0.0/0.0.0.0
http_acess allow all


[COLOR="Red"]NOTE:  I am using putty from a windows machine (192.168.0.3)  to make a sshd tunnel and proxy my webbrowser through squid.   Like I said, it only works when I configure squid to "allow all".   If I try to make my own ACL name and then allow that, then the browser is presented with a page that says the browser isnt allowed access to the proxy server.[/COLOR]

---

### Post by mozkill on 2007-12-13
please, I would be grateful for ANY help at all...

---

