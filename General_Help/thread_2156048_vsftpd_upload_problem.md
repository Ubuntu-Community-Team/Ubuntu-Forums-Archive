---
title: "vsftpd upload problem"
date: 2013-06-20
forum: General Help
---

### Post by mickey13 on 2013-06-20
I'm using vsftpd version 3.0.2.  I'm using FTPeS.  I have the control port and data port range open on both my server's software firewall, and my router's firewall.  I can connect and download a file, but I'm having problems uploading a file.  The file acts like it actually uploads, but I get the error "426 Failure writing network stream".  I found a resource that says to set use_sendfile=NO, but that didn't help.  Has anyone else seen this and found a solution?  Thanks.

---

### Post by mickey13 on 2013-06-20
I did notice that I can upload and download fine when I'm on the LAN, and that the problem happens when I access via Internet.  To me this would indicate a firewall or router issue, but the ports are open; I've checked, double-checked, triple-checked, etc.  I looked through the router config for anything that would filter out FTP connections, and didn't find anything.  Could it still be some sort of data sabotage built into the router (or maybe even cable modem), or some Ubuntu security policy?

Given the behavior, I think I can rule out SSL config error, file system permissions, FTP client problem (I've tried lftp, BitKinex, FileZilla, and I have a problem with all of them).  I want to rule out firewall ports being the problem because I've checked that so many times.  I want to say it is a problem in my /etc/vsftpd.conf and I just don't know what setting is screwing things up for me, but since I can connect and transfer files fine on the LAN, I feel like that's not the problem.  My best guess right now is that there is some other router, or Ubuntu policy causing the above error.  Thoughts?

---

