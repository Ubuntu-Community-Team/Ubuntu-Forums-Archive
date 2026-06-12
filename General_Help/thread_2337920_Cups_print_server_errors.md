---
title: "Cups print server errors"
date: 2016-09-22
forum: General Help
---

### Post by Aphexlog on 2016-09-22
Hello all,

I have configured a cups print server on a ubuntu 14.04 server and I have gone through the web interface as my root user to add the required printer.
i am able to send a test print to the printer just fine via the web interface (<ip address>:631).
I am using a POS device (I pad) to send the print job to the server... and the issue is that I am unable to print via this method
I believe that the issue is with the server, not the device that I am using.
I had to use a .ppd file for the print drivers when adding this printer.
Now when trying to print I receive the following error in the /var/log/cups/error_log as soon as I start up the cups service: 

W [22/Sep/2016:14:24:26 -0500] CreateProfile failed: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [22/Sep/2016:14:24:31 -0500] CreateProfile failed: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [22/Sep/2016:14:24:36 -0500] CreateDevice failed: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
vmadmin@x8qa-engage02:/etc/cups$ tail -f /var/log/cups/error_log
W [22/Sep/2016:14:24:26 -0500] CreateProfile failed: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [22/Sep/2016:14:24:31 -0500] CreateProfile failed: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [22/Sep/2016:14:24:36 -0500] CreateDevice failed: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
******************************************************

Might anyone have suggestions?

Thanks in advance.

---

### Post by Aphexlog on 2016-09-22
Never mind everyone! 
Enabling 'browsing' in the cupsd.conf resolved this error

---

