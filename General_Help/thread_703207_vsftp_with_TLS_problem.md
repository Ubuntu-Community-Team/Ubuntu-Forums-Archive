---
title: "vsftp with TLS problem"
date: 2008-02-21
forum: General Help
---

### Post by dexter2 on 2008-02-21
Hi,
my vsftp server was working fine. Than i added TLS encryption. Server is in another subnetwork (DMZ) and there is firewall  in between LAN and DMZ. I use Total Commander to log in to server. When I connect from LAN network it is working fine, but when I connect from Internet it gives this error: 500 Illegal PORT command.
The whole log looks like this:
=======================================================
Thu Feb 21 10:03:53 2008 [pid 1412] CONNECT: Client "114.21.27.151"
Thu Feb 21 10:03:53 2008 [pid 1412] FTP response: Client "114.21.27.151", "220 (vsFTPd 2.0.5)"
Thu Feb 21 10:03:53 2008 [pid 1412] FTP command: Client "114.21.27.151", "?Z????Q??? ??9??8??5????????"
Thu Feb 21 10:03:53 2008 [pid 1412] FTP response: Client "114.21.27.151", "530 Please login with USER and PASS."
Thu Feb 21 10:04:20 2008 [pid 1414] CONNECT: Client "114.21.27.151"
Thu Feb 21 10:04:20 2008 [pid 1414] FTP response: Client "114.21.27.151", "220 (vsFTPd 2.0.5)"
Thu Feb 21 10:04:21 2008 [pid 1414] FTP command: Client "114.21.27.151", "AUTH TLS"
Thu Feb 21 10:04:21 2008 [pid 1414] FTP response: Client "114.21.27.151", "234 Proceed with negotiation."
Thu Feb 21 10:04:22 2008 [pid 1414] FTP command: Client "114.21.27.151", "USER userftp"
Thu Feb 21 10:04:22 2008 [pid 1414] [userftp] FTP response: Client "114.21.27.151", "331 Please specify the password."
Thu Feb 21 10:04:22 2008 [pid 1414] [userftp] FTP command: Client "114.21.27.151", "PASS <password>"
Thu Feb 21 10:04:22 2008 [pid 1413] [userftp] OK LOGIN: Client "114.21.27.151"
Thu Feb 21 10:04:22 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "230 Login successful."
Thu Feb 21 10:04:22 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "SYST"
Thu Feb 21 10:04:22 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "215 UNIX Type: L8"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "FEAT"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "211-Features:"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " AUTH SSL??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " AUTH TLS??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " EPRT??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " EPSV??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " MDTM??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " PASV??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " PBSZ??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " PROT??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " REST STREAM??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " SIZE??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", " TVFS??"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "211 End"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "PBSZ 0"
Thu Feb 21 10:04:23 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "200 PBSZ set to 0."
Thu Feb 21 10:04:24 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "PROT P"
Thu Feb 21 10:04:24 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "200 PROT now Private."
Thu Feb 21 10:04:24 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "PWD"
Thu Feb 21 10:04:24 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "257 "/home/userftp""
Thu Feb 21 10:04:25 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "TYPE A"
Thu Feb 21 10:04:25 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "200 Switching to ASCII mode."
Thu Feb 21 10:04:25 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "PORT 10,128,31,68,7,108"
Thu Feb 21 10:04:25 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "500 Illegal PORT command."
Thu Feb 21 10:04:25 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "PASV"
Thu Feb 21 10:04:25 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "227 Entering Passive Mode (118,64,10,13,120,226)"
Thu Feb 21 10:04:28 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "PORT 10,128,31,68,7,110"
Thu Feb 21 10:04:28 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "500 Illegal PORT command."
Thu Feb 21 10:04:34 2008 [pid 1416] [userftp] FTP command: Client "114.21.27.151", "QUIT"
Thu Feb 21 10:04:34 2008 [pid 1416] [userftp] FTP response: Client "114.21.27.151", "221 Goodbye."
======================================

Thanks for help 
    Dexter

---

### Post by dexter2 on 2008-02-21
so the problem was passing through firewall. Firewall is unable to track encrypted connection, so it won't let pass ftp-data passive connection. I did as said here: 
[http://www.davekb.com/browse_computer_tips:vsftpd_tls_setup_that_works:txt](http://www.davekb.com/browse_computer_tips:vsftpd_tls_setup_that_works:txt)

---

