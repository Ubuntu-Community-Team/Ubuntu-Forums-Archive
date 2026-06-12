---
title: "postfix + dovecot + mysql (virtual users and domains) cannot connect 3rd party client"
date: 2013-10-14
forum: General Help
---

### Post by eagles051387 on 2013-10-14
I have a multiple domain email setup with virutal domains and users and for some reason 3rd party mail clients are not able to connect. The web mail works fine as well as sending and recieving of emails.

Any links would be greatly appreciated.

Regards

---

### Post by L486XGW on 2013-10-17
Check your firewall. Are you talking about imap or what?

---

### Post by SeijiSensei on 2013-10-17
If you are using a web interface on the same machine, it will be communicating with the IMAP or POP3 server (dovecot, UW-imap, etc.) over the "localhost" interface, 127.0.0.1.  Depending on the security settings, particularly the "listen" parameter in dovecot.conf, that may be the only interface it is listening on.  A quick check is to run the command "telnet 10.10.10.10 143" replacing "10.10.10.10" with the IP address of the Internet-facing interface on the machine.  If it can connect, the problem is likely a closed port because of firewalling.  To check that, try the same command from another machine outside your local network.

On the unlikely chance that your server is running only POP3, replace "143" above with "110".

---

