---
title: "copy a file to more than one computer on linux"
date: 2006-11-09
forum: General Help
---

### Post by earobinson on 2006-11-09
I have a large file on my linux network (larger than 10 gigs) and I want to copy it to multiple computers (more than 10). Now the computers are set up so they can ssh into each other without passwords so I was thinking I could write a script to scp it to each computer, but that would take a long time. Is there any way that i could do a broadcast scp so that I could copy this file to all the computers at the same time, or any other way to copy the file quickly to all the computers a the same time instead of each one individually.

Thanks

---

### Post by kidders on 2006-11-09
Hi there,

SSH connections can't be broadcast, because they're encrypted. (If you want copy operations to go faster, you should choose a protocol that isn't encrypted anyway.)

If it were me, I'd try running two or three copies concurrently, rather than just one at a time. Depending on your specific systems, that may go faster. Also, having performed the copy once, you'd then have two sources to copy the file from. If your network is well laid out, that may also reduce the amount of time it takes to finish.

Any help?

---

### Post by earobinson on 2006-11-09
> **kidders said:**
> Hi there,

SSH connections can't be broadcast, because they're encrypted. (If you want copy operations to go faster, you should choose a protocol that isn't encrypted anyway.)

If it were me, I'd try running two or three copies concurrently, rather than just one at a time. Depending on your specific systems, that may go faster. Also, having performed the copy once, you'd then have two sources to copy the file from.

Any help?
Yup I can copy about 3 at a time. any sugestions on another program to use?

---

### Post by kidders on 2006-11-09
Plain old FTP might be your best bet. That would also let you start a handful of the copies client-side from, say, a web browser. Be careful though ... if you have lots of hubs on your LAN, too many overloaded switches, or a slow hard disk on the source computer(s), concurrent copies can be slower.

---

### Post by earobinson on 2006-11-09
> **kidders said:**
> Plain old FTP might be your best bet. That would also let you start a handful of the copies client-side from, say, a web browser. Be careful though ... if you have lots of hubs on your LAN, too many overloaded switches, or a slow hard disk on the source computer(s), concurrent copies can be slower.
I assume this can be done from the command line to?

---

### Post by kidders on 2006-11-09
Yes, assuming you have a suitable FTP client (or a server, I suppose!) available on the destination machines. Wget might even do the job for you.

---

### Post by earobinson on 2006-11-09
> **kidders said:**
> Yes, assuming you have a suitable FTP client (or a server, I suppose!) available on the destination machines. Wget might even do the job for you.
Any recomendations for a good ftp server?

---

### Post by kidders on 2006-11-09
For your purposes, it makes very little difference, since you will most likely be deleting it within hours of installing it.

I wouldn't fuss too much over it ... bear in mind that even a copy over samba (at approx. 10MB/s) would only take 3 hours, even if you copied the file onto each of your 10 computers one at a time. Don't spend too much time trying to concoct clever ways of doing it!

---

