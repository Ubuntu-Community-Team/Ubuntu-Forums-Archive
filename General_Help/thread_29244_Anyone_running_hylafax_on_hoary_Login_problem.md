---
title: "Anyone running hylafax on hoary? Login problem"
date: 2005-04-23
forum: General Help
---

### Post by fevzinet on 2005-04-23
I cannot send fax through hylafax server.

Am i doing sth wrong?


//////////////////////////////////////////////////////////////////////////////////
root@ysalk:/home/yelizsalk # faxsetup
ln: `bin/bin': File exists
/home/yelizsalk

Setup program for HylaFAX (tm) 4.2.0.

Created for i686-pc-linux-gnu on Tue Dec 14 22:54:52 GMT 2004.

Reading cached parameters from /var/spool/hylafax/etc/setup.cache.

Checking system for proper server configuration.


Warning: /etc/hylafax/vgetty-link does not exist or is not an executable program!

The file:

    /etc/hylafax/vgetty-link

does not exist or this file is not an executable program.  The
HylaFAX software optionally uses this program and the fact that
it does not exist on the system is not a fatal error.  If the
program resides in a different location and you do not want to
install a symbolic link for /etc/hylafax/vgetty-link that points to your programthen you must reconfigure and rebuild HylaFAX from source code.

Make /var/spool/hylafax/bin/ps2fax a link to /var/spool/hylafax/bin/ps2fax.gs.


Make /var/spool/hylafax/bin/pdf2fax a link to /var/spool/hylafax/bin/pdf2fax.gs.
Update /var/spool/hylafax/status/any.info.

        HylaFAX configuration parameters are:

        [1] Init script starts faxq:            yes
        [2] Init script starts hfaxd            yes
        [3] Start old protocol:                 no
        [4] Start paging protocol:              no
Are these ok [yes]?

Modem support functions written to /var/spool/hylafax/etc/setup.modem.
Configuration parameters written to /var/spool/hylafax/etc/setup.cache.

Restarting HylaFAX server processes.

You have a HylaFAX scheduler process running.  faxq will be
restarted shortly, as soon as some other work has been completed.
Can I terminate this faxq process (23426) [yes]?
Should I restart the HylaFAX server processes [yes]?

/etc/init.d/hylafax start
Not starting HylaFAX daemons since they are already running.

Looks like you have some faxgetty processes running (PIDs are):

    23439

It is usually a good idea to restart these processes after running
faxsetup; especially if have just installed new software.  If these
processes are being started by init(8) then sending each of them a
QUIT message with the faxquit command should cause them to be restarted.
Is it ok to send a QUIT command to each process [yes]?
/usr/sbin/faxquit ttyS0

Done verifying system setup.
/usr/lib/hylafax/bin/copy_configuration_from_spool: line 36: [: too many arguments
Updating /etc/hylafax/setup.cache from /var/spool/hylafax/setup.cache.
Updating /etc/hylafax/setup.modem from /var/spool/hylafax/setup.modem.
/var/spool/hylafax
//////////////////////////////////////////////////////////////////////////////////////////
//////////////////////////////////////////////////////////////////////////////////////////



root@ysalk:/home/yelizsalk # sendfax -f "localhost" -R -r "faxsubject" -c "coverpage comments" -x "Recipient's company" -d "Recipient@21" /home/yelizsalk/1.pdf Password:
Login failed: 500 'PASS ': Syntax error, expecting password.
root@ysalk:/home/yelizsalk # sendfax -f "localhost" -R -r "faxsubject" -c "coverpage comments" -x "Recipient's company" -d "Recipient@21" /home/yelizsalk/1.pdf
Password:
Login failed: 530 Login incorrect.
root@ysalk:/home/yelizsalk #

---

