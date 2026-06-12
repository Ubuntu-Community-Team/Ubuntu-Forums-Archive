---
title: "FTP Using SSH Tunnel / Webmin / ProFTPD"
date: 2007-09-06
forum: General Help
---

### Post by rpalmer on 2007-09-06
The FTP works internally but when I try to connect to it remotely it does not work.  A port has been opened on my router for port 22 and forwarded to the correct internal IP address.  I'm sure I have Putty and the router set up right because I get prompted for a user id and password but it never establishes a data connection.  here are the logs for ProFTPD.

Sep 06 12:50:45 rypp-ubuntu704 proftpd[27115] rypp-ubuntu704: ProFTPD 1.3.0 standalone mode SHUTDOWN
Sep 06 12:50:45 rypp-ubuntu704 proftpd[27177] rypp-ubuntu704: ProFTPD 1.3.0 (stable) (built Thu Mar 8 03:01:15 UTC 2007) standalone mode STARTUP
Sep 06 12:50:53 rypp-ubuntu704 proftpd[27182] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): FTP session opened.
Sep 06 12:50:53 rypp-ubuntu704 proftpd[27182] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): mod_delay/0.5: delaying for 16 usecs
Sep 06 12:50:53 rypp-ubuntu704 proftpd[27182] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): USER rpalmer: Login successful.
Sep 06 11:50:53 rypp-ubuntu704 proftpd[27182] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): Preparing to chroot to directory '/media/disk'
Sep 06 11:50:53 rypp-ubuntu704 proftpd[27182] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): mod_delay/0.5: delaying for 734 usecs
Sep 06 11:51:01 rypp-ubuntu704 proftpd[26805] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): Data transfer stall timeout: 600 seconds
Sep 06 11:51:01 rypp-ubuntu704 proftpd[26805] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): FTP session closed.
Sep 06 12:51:46 rypp-ubuntu704 proftpd[27223] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): FTP session opened.
Sep 06 12:51:46 rypp-ubuntu704 proftpd[27223] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): mod_delay/0.5: delaying for 19 usecs
Sep 06 12:51:46 rypp-ubuntu704 proftpd[27223] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): USER rpalmer: Login successful.
Sep 06 11:51:46 rypp-ubuntu704 proftpd[27223] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): Preparing to chroot to directory '/media/disk'
Sep 06 11:51:46 rypp-ubuntu704 proftpd[27223] rypp-ubuntu704 (rypp-ubuntu704.local[192.168.4.5]): mod_delay/0.5: delaying for 409 usecs

Let me know if anyone has any ideas...

---

### Post by kevstar31 on 2007-09-06
Did you try using an sftp client?

---

### Post by rpalmer on 2007-09-06
I am using FileZilla on a windows machine and it has sftp capabilities.  Can you recommend a good one?

---

### Post by robrmd9 on 2007-09-06
FTP generally runs on port 21 (unless you changed it), and port 22 is usually for SSH.  So I would try opening port 21, and then trying FTP again if you want normal FTP.  If you are trying to login via SSH (which I think you are), then check your client's settings because the traffic should go through port 22 without port 21 needing to be open.

Edit:  Filezilla is a great client for FTP/SFTP, so you shouldn't need a different one.

---

### Post by rpalmer on 2007-09-06
The FTP server is currently running on port 21.  Port 21 is not being forwarded through the router.  I actually left only port 22 open on purpose because I wanted to make sure that when I finally got connected to the ftp through the SSH tunnel that I was in fact using port 22 and not connecting on port 21.  

PuTTy is set up as follows:
-SESSION-
Hostname or IP address: <external IP> port 22
Connection type is SSH

-SSH | TUNNELS -
Source Port: 48731
Destination: 192.168.10.5:21
IPv4

FTP Client connects with the below information along with the user id and password of course.
127.0.0.1:48731


It's weird that I can connect to the FTP from the internal network with no problems It's also strange that through the SSH tunnel it prompts me for a username/password but won't establish a data connection.  On the FTP Server I've tried enabling and disabling passive ports, enabling and disabling masquerade address and commenting out any IPv6 entries in the config file because i wanted to make sure it wasn't using IPv6.

---

### Post by rpalmer on 2007-09-07
I also wanted to add that just out of curiosity, I opened port 21 to try and establish a normal ftp session without putty to see if my router was properly configured and it in fact worked fine.  This confirms that the ftp server is set up correctly and that port forwarding on my firewall is set up correctly.

I am going to analyze my settings in putty a little more carefully or maybe try establishing a ssh tunnel using a different method.

---

