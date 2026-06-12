---
title: "Download files to network storage issues."
date: 2013-04-19
forum: General Help
---

### Post by SASDOE2 on 2013-04-19
Hi all, 

Here is my problem, hopefully someone will have an answer :

Just bought a raspberry pi, I want to use it to download files with deluge and save the files to a home server. This server runs both ftp and webdav, but both transfer methods are slower than the deluge download, so it can't keep up and ends up failing (deluge outputs a "file too short" error. Eeasiest solution would be to find a fast enough transfer method (if any, but given I can download as fast as 10M/s I has to be way faster as to never ever error, so I am not convinced this is the most reliable one.

I happen to own a 160g purposless drive. I would like to set this up so the rpi downloads to this drive.

I see two options :

 - I have deluge or another system move the completed files to the server, problem is this means I can't have more than 160g of simultaneous downloads. Wouldn't this network file moving process be too harsh on the rpi? 

- I can somehow connect the rpi directly to the server (physically I mean) so transfer speeds are equivilant to the drive being connected to the rpi. How could I do this ? Is it possible? 

What would work best ? Any ideas how ? 

Thnaks for your times guys !

---

### Post by scbingham on 2013-04-19
Fastest physical connection would probably be an ethernet cable. Pi model B has 10/100Mb port.

---

### Post by SASDOE2 on 2013-04-19
Ok and how do I mount the drives ? Cheers for the help !

---

### Post by scbingham on 2013-04-19
This looks interesting:
[http://www.linuxnix.com/2011/03/mount-directory-locally-linux-sshfs.html](http://www.linuxnix.com/2011/03/mount-directory-locally-linux-sshfs.html)

---

### Post by SASDOE2 on 2013-04-19
God I've been fidgiting with a blooy annoying script that I can't seem to run on boot from /etc/network/if-up.d/script, this looks like a nice alternative ! Cheers !

EDIT : And scratch that, working at last. The magic of forums !!

---

