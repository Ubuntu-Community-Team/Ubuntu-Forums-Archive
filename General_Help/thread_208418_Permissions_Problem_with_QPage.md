---
title: "Permissions Problem with QPage"
date: 2006-07-03
forum: General Help
---

### Post by hogihung on 2006-07-03
I have an external modem connected to my new Ubuntu 6.06 box.  Spent a bit of time making sure it worked - thanks to reading many posts here.

Been trying for several hours to get QPage to work and finally decided to reach out here.  Looking thru my daemon.log file I found:

> Jul  3 14:49:01 jsm-mon qpage[5479]: giving up root privileges
Jul  3 14:49:01 jsm-mon qpage[5479]: /etc/qpage.cf(71): cannot access /dev/ttyS1
: Permission denied
Jul  3 14:49:01 jsm-mon qpage[5479]: /etc/qpage.cf(73): no device for modem=ttyb


From my qpage.cf I have:
> queuedir=/var/spool/qpage

identtimeout=5
snpptimeout=60

modem=ttyb device=/dev/ttyS1

service=default
        device=ttyb
        baudrate=1200
        parity=even
        allowpid=yes
        maxtries=6
        maxmsgsize=254
My guess is when qpage is being called either the process calling doesn't have permissions, or qpage doesn't have permissions to the modem.  I'm new to Linux so please be gentle.

Thanks,

Ho...

ps. reading thru the forums, I used wvdial to test the modem and thankfully it works fine.

---

### Post by hogihung on 2006-07-03
Well I figured it out - a relatively dumb mistake on my part.  I'll post some info below in case it will help someone else in the future. 

> sudo /usr/bin/qpage -d -Q
giving up root privileges
becoming user 'uucp'
/etc/qpage.cf(71): cannot access /dev/ttyS1: Permission denied
/etc/qpage.cf(73): no device for modem=ttyb
Error reading configuration file

I had added the uucp user to the dialout group, but realized I never saved the settings by closing out of the application.  Once I did this, and re-ran qpage I get this:

> sudo /usr/bin/qpage -d -Q
giving up root privileges
becoming user 'uucp'
The page queue is empty.

Once I saw it was working correctly I restarted qpage by issuing:
sudo /etc/init.d/qpage start.

Now MON and QPage are working as intended.  On to my last problem to solve - moncgi and authenticating.

Ho...

---

