---
title: "Network scanner is not working via Sane-pixma (Xsane, SimpleScan)"
date: 2016-02-26
forum: General Help
---

### Post by willyn2 on 2016-02-26
Hi,

I am trying to get the scanner of my canon multi-functional mf8350cdn  working via my network. I installed the latest Linux printer drivers of  Canon and I found that the Canon i-sensys mf8300 series is supported via  sane-pixma backend. The printer is working fine, but when I try to find  my scanner via scanimage -L I get an error.  I followed all instruction  available to install a network scanner and it seems to work fine except  that I have an issue with the naming convention of sane-pixma. 

At the man page of the website [http://linux.die.net/man/5/sane-pixma](http://linux.die.net/man/5/sane-pixma) I read the following:
"[COLOR=#0000cd]Device names for BJNP devices is in the form  pixma:aaaa_bbbbb where aaaa  is the scanners model and bbbb is the  hostname or ip-adress.[/COLOR]"

However the separator : is the same as the one used to add a port to the scanner. So when I apply this syntax [COLOR=#0000cd](bjnp://pixma:mf8300_192.168.1.104)[/COLOR]  in the pixma.conf, it doesn't find the scanner as it searches for the  scanner "pixma" at port mf8300_192.168.1.104. If I use a _ instead of :  it doesn't recognize it either or putting the string between brackets  doesn't help too. 

Does anybody know what syntax I need to use in the pixma.conf to apply the right sane backend and get the scanner working?

---

