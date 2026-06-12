---
title: "Brother  5150D Printer not working over samba"
date: 2007-01-04
forum: General Help
---

### Post by patpicos on 2007-01-04
Hi Folks,

I just bought a Brother 5150D printer over the holidays as it offers duplex printing.
I am able to print duplex from linux (kubuntu 6.06LTS). However I am unable to print from my windows clients.

I am using the foomatic/HPijs driver in linux as it is the fastest to give me a printout and offer duplexing. The driver provided by brother is too slow.

My samba config goes as follows

> 
root@server:/etc/samba# cat smb.conf
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/01/04 17:09:15

[global]
        passwd program = /usr/bin/passwd %u
        passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*
        username map = /etc/samba/smbusers
        unix password sync = Yes
        log level = 4
        log file = /var/log/samba/%m.log
        max log size = 50
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = /etc/printcap
        dns proxy = No
        ldap ssl = no
        hosts allow = 192.168.2.
        cups options = raw

[homes]
        comment = Home Directories
        read only = No
        browseable = No

[video]
        path = /data/video
        read only = No
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = Yes
        use client driver = Yes
        browseable = No

[tmp]
        comment = Temporary file space
        path = /tmp
        read only = No
        guest ok = Yes



[Brother_HP]
        comment = BROTHER HL-5150D with hpijs driver
        path = /var/spool/samba
        read only = No
        guest ok = Yes
        printable = Yes
        printing = cups
        printer name = Brother_HP
        use client driver = Yes
        oplocks = No
        share modes = No
root@server:/etc/samba#


I am able to install the printer from my windows clients, but when sending a print job, it doesnt print. Its like it goes to never land. Also, getting the printer properties takes forever.
Also, when bringing up the print window in any windows application (firefox, ie, word) once i select the Brother printer.....it freezes up....

On the windows side, i use the driver provided on the cd (PCL-English)


Any1 has ideas to get my windows machines to print properly (XP SP2 and 2003 server).

I used to have a Samsung ML-1430 and it worked like a charm.....

---

### Post by watlings on 2007-01-07
I came across your message while troubleshooting my own Samba problems on ubuntu with a brother HL5150D (really nice printer, BTW.  the standard PS drivers that come w/Ubuntu work just fine for me)  anyway.. there isn't quite enough information here to know if you have the same problem I have for sure, but check out my post here:

[http://www.linuxquestions.org/questions/showthread.php?p=2575549#post2575549](http://www.linuxquestions.org/questions/showthread.php?p=2575549#post2575549)

It might point you in a new direction.  Hope this helps, and good luck!:)

---

### Post by peterLinux on 2007-01-07
Not sure but
cups options = raw
and
use client driver = Yes

Means you are using the driver on the windows clients no?

I just got my feet wet with ubuntu and sambe 
found this helpful:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

Peter

---

