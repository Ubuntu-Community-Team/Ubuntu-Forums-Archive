---
title: "Suddenly lost external access to mailserver, smtp, web server, sshd"
date: 2014-10-30
forum: General Help
---

### Post by Phiwum on 2014-10-30
Hello.

I've been running my own mail and web server for years, with nary a hitch.  Yesterday, however, I realized that I couldn't access my IMAP server from outside the network.  A little investigation showed that the same was true for the web server and ssh daemon.  Moreover, I'm not receiving emails from outside the LAN, so I think that I have the same problem with the SMTP server (?).  

I use iptables, fail2ban and knockd (for port knocking).  I don't see anything suspicious in the logs for these.  It is clear that I can knock the machine (on random ports, not used for any standard services), and once I have knocked, I can ping the machine.  

I called my ISP (RCN) and they confirmed that they are not filtering any ports (I have a static IP address, so all ports should be open).

I have no problem logging into the IMAP server, viewing web pages, SSH'ing into the machine or sending mail on the local network.  The only issue is on the external interface.  None of these ports are showing up in the firewall log, which logs every package dropped.

I'm bumfuzzled.  Any help diagnosing the problem would be appreciated.  Please let me know what data is relevant.

Thanks much.

---

### Post by Phiwum on 2014-10-30
The problem was apparently on my ISP's end.

Further investigation suggested that packets outgoing on ports 80, 25, 22 and 993 (and others?) were not reaching their destination -- perhaps an outgoing filter, though apparently unintentional on the part of my ISP[1].  Other ports were unaffected, so I could use the SSH server by moving it to a random unused port (1313, say).  

The problem just went away after about 36 hours.  Maybe something was rebooted, maybe others complained about similar problems and got it fixed, but it just started working after a while.

[1] In fact, my ISP (RCN) filters dynamic IPs, but only ports 25 and 80, so how those other ports were filtered (if that's the right diagnosis) really is a bit bumfuzzling.

---

