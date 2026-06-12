---
title: "CUPS Server With Archiving"
date: 2013-04-15
forum: General Help
---

### Post by dpkubu on 2013-04-15
I have installed a lubuntu machine as a cups based print server, I would like to maintain a backup of all documents printed on connected printers in PDF for compliance with name of user / source IP 

I have a A3 size HP k850 & HP MFD M1005 conncted to it.

help is appreciated

Deepak

---

### Post by tgalati4 on 2013-04-15
There are settings in the cups configuration file to allow this.

```
man cupsd.conf
```

       PreserveJobFiles Yes

       PreserveJobFiles No

There are probably a few other switches needed as well, such as job history.

---

