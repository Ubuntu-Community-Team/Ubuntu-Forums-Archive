---
title: "Brother printer issue"
date: 2014-05-12
forum: General Help
---

### Post by vik2 on 2014-05-12
Hello all, just dumped windows for Ubuntu yesterday. I have a Brother DCP-375CWprinter to which Ubuntu recognises but does not allow me to print. I've tried the generic recommended driver to no avail, went to Brother support and tried to download the Linux printer driver but it says it's a bad package install on Ubuntu software centre, I click continue but doesn't installdriver. It did install the cwcup driver and it's on the database. When I select any DCP driver from Ubuntu's printer database the printer panel says receiving data but does not print. Every time I test print it says a different job number. Help, anyone?

---

### Post by gifford on 2014-05-12
Welcome to the forum! 
I would recommend going back to the Brother site and download the drivers and then follow the instructions to install by the command line.
Make sure you have all the pre install recommendations done as listed on the Brother site.
Sometimes printer installations can be frustrating but I have never had a problem using the instructions on the Brother site.

---

### Post by pdc on 2014-05-12
so vik;

Brother provide two packages for a printer driver: LPR and CUPSWRAPPER:

plan is: you install 

1) LPR and then 
2) CUPSWRAPPER

_______________________

when one clicks to download, it is then that the instructions are revealed: in all their glory (I attach a screenshot):

and that is where it gets more tricky;

__________________

**_so tell us_**....................**are you using a 64bit system?** (if you are not sure type > [COLOR="#FF0000"]arch[/COLOR] in a terminal: i686=32bit )

______________________________________________

there are 2 ways to go to install the Brother drivers: gifford is very knowledgable about Brother and always advises using CLI

on the other hand, Brother have made available an install tool; that one can run..........that *should*.............. get the right drivers.............work out if you have 64bit..........and do all the needed..................seems like a good way to go ...

---

### Post by vik2 on 2014-05-12
Thanks for the advise all, all sorted out. Got thinking if I'm doing the software install right must be the firewall as advised on pdc's info attachments. I run a firewall so I made a limited rule for the printer and all good. It's 64bit Ubuntu.

---

