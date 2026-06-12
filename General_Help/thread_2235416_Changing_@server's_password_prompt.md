---
title: "Changing @server's password prompt"
date: 2014-07-20
forum: General Help
---

### Post by sartoph on 2014-07-20
I noticed when I log into a server I recently built, when I log into the server I get prompted with:
[EMAIL="username@www.url.com's"]username@www.url.com's[/EMAIL] password:
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-57-virtual x86_64)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Mon Jul 21 12:18:33 2014
[EMAIL="username@hostname:~$"]username@hostname:~$[/EMAIL]

I'm trying to work out where the **@www.url.com's** password part is set when I type in a username. Not sure how on earth I set it :)

---

### Post by tgalati4 on 2014-07-20
```
cat /etc/hostname
```

tgalati4@Mint14-Extensa ~ $ cat /etc/hostname
Mint14-Extensa
tgalati4@Mint14-Extensa ~ $ man hostname
tgalati4@Mint14-Extensa ~ $ which hostname
/bin/hostname
tgalati4@Mint14-Extensa ~ $ apropos hostname
BIO_get_conn_hostname (3ssl) - connect BIO
BIO_set_conn_hostname (3ssl) - connect BIO
freehostent (3)      - get network hostnames and addresses
gethostname (2)      - get/set hostname
getipnodebyaddr (3)  - get network hostnames and addresses
getipnodebyname (3)  - get network hostnames and addresses
hostname (1)         - show or set the system's host name
hostname (7)         - hostname resolution description
hosts (5)            - static table lookup for hostnames
sethostname (2)      - get/set hostname
ssh-argv0 (1)        - replaces the old ssh command-name as hostname handling

Welcome to the forums.  No dumb questions, only dumb answers.

---

### Post by sartoph on 2014-07-20
thanks, it's different to the hostname on the server, as you can see when I log in it's displays username@hostname, but when I log in, it displays username@url , I looked in the hostname file but only display the hostname details as you would expect.

---

### Post by Habitual on 2014-07-21
check .bashrc for PS variables' strings.

---

### Post by steeldriver on 2014-07-21
It looks like you are referring to the **ssh **password prompt - which in turn comes from PAM, I think.

 I'm not aware of any way of changing it short of modifying the source.

---

