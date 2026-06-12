---
title: "[SOLVED] LTSP on 16.04: TFTP open timeout"
date: 2017-06-06
forum: General Help
---

### Post by v4169sgr on 2017-06-06
Hello,

Posting this here as some of the solutions I have seen don't appear to be applicable to me.

I am running LTSP-PNP on 16.04 32 bit.

I've followed these instructions to get going:

[https://help.ubuntu.com/community/UbuntuLTSP/ltsp-pnp](https://help.ubuntu.com/community/UbuntuLTSP/ltsp-pnp)

supplemented by these instructions (scroll down: second half) to create a dnsmasq config

[https://wiki.debian.org/LTSP/Howto](https://wiki.debian.org/LTSP/Howto)

My problem now is that clients on start up are timing out when looking for the TFTP server.

None of these directions mention a TFTP server.

What am I missing?

Thanks :)

---

### Post by v4169sgr on 2017-06-06
UPDATE:

I managed to step around this error by following step 4 in the guidance from the Debian LTSP Howto:

> If the server will run one subnet containing the Internet connection and the clients it need have only one network interface card. In this case dnsmasq can be configured to run a dhcp-proxy if there already is another dhcp server active. In this case edit the above file to comment out the dhcp range line and ensure there is a line (uncommented) stating dhcp-proxy.

The thin client now boots and arrives at the LDM login prompt. However, the login is not accepted, and inspection of /var/log/syslog shows:

```
Jun  6 12:12:48 aammscott nbd_server[2734]: Can't open authorization file /etc/ltsp/nbd-server.allow (No such file or directory).
```

I tried working around this by touching the ndb-server.allow file, but ran into problems with the nbd server not being able to serve.

What should be in this file?

---

### Post by v4169sgr on 2017-06-06
UPDATE #2: With the help of "||cw" on #ltsp in freenode, it turns out the problem is to do with trying to load a unity image on the clients, which then barf.

Installing ubuntu-mate-desktop resolved the issue: users on the clients select 'MATE' as their desktop, and are then able to log in.

---

