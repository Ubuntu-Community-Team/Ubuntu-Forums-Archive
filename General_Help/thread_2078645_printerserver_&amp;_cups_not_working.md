---
title: "printerserver &amp; cups not working"
date: 2012-10-31
forum: General Help
---

### Post by somethrowawayname on 2012-10-31
I want to forward print to a network cups server. The printers do not appear in the print menu of any GUI program. The server is known to be working with lots of pcs so the problem is most certainly on the client end.

Suppose the hostname is printserver. I can reach the server using ping printserver as well as entering printserver:631 in a browser. I have cups installed locally and running. I can reach the local cups using localhost:631.

I have created the file /etc/cups/client.conf and entered

```
ServerName printserver
```

When I enter lpstat -H on the consol I get

```
printserver:631
lpstat: Bad Request
```

lpstat -l just outputs

```
lpstat: Bad Request
```

The local cups version is 1.6.1. The server cups version is 1.3.7.

Does someone have an idea where the problem is?

---

### Post by somethrowawayname on 2012-10-31
After some research I have found out that my client is the only one with a 1.6.* cups version. Is there some easy way to downgrade it to a 1.5.* version in Ubuntu 12.10 ?

---

### Post by somethrowawayname on 2012-11-01
Does no one have an idea? Am I the only one with this problem? :(

---

### Post by somethrowawayname on 2012-11-04
*bump*

---

### Post by somethrowawayname on 2012-11-06
*rebump*

---

### Post by dshrek on 2012-11-19
Same problem here. I filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1080640](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1080640)

Any new suggestions?

---

