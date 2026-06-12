---
title: "lpadmin problem"
date: 2007-06-21
forum: General Help
---

### Post by dryder on 2007-06-21
Hi,
Feisty

Following the instructions here [COLOR="Blue"][https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)[/COLOR], on step
> **4.**
...
$ sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
I substitute $ sudo /usr/sbin/lpadmin -p LBP3000 -P CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E

and get:
**[COLOR="Red"]lpadmin: No such file or directory[/COLOR]**

(I have substituted my printername and drivername as instructed and followed the *Note: If you get the error lpadmin: Unable to copy PPD file!*, try substituting -P for -m above. ).

Please can anybody help with this error?

Many thanks,
David

---

### Post by AlexThomson_NZ on 2007-06-22
That looks like ldapadmin has not been installed.  Can you verify there is an ldapadmin command in /usr/sbin?

---

### Post by dryder on 2007-06-22
Hi AlexThomson_NZ,

yes there is - which is what puzzled me 	:confused:
and I have other printers install OK ... but via Systemm>Printers>add printer ...


(I assume you mean lpadmin)

---

### Post by AlexThomson_NZ on 2007-06-22
Ahh yes- been doing too much ldap sys admin stuff lately :)

Well that command is definitely trying to look for something and failing- maybe the ppd file or the device?

I assume the ppd file is in your working directory- is "ccp:/var/ccpd/fifo0 valid"?

---

### Post by dryder on 2007-06-22
> is "ccp:/var/ccpd/fifo0 valid"?

/var/ccpd/fifo0 is valid but I am not sure what the prefix ccp: means.

I wish there was an easy way to uninstall/re-install all of lpadmin, CUPS etc, etc, printers and ALL related driver files so I could start again  :(

---

### Post by AlexThomson_NZ on 2007-06-22
ccp is "command control protocol" and is used to communicate to things like printers, etc.

---

