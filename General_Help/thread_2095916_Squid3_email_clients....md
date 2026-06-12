---
title: "Squid3 email clients..."
date: 2012-12-18
forum: General Help
---

### Post by lestertorres on 2012-12-18
Hello everyone, I first want to thank you all that reply to my post in advance. 

I have a squid proxy installed with an isc-dhcp-server as well and it is working awesome. I have put a whitelist to work with the proxy and it is doing its job but I am having an issue with connecting the proxy to email clients. I have tried with Thunderbird (linux machine) and Outlook (windows machine through a swtich) and no luck at all. I know that a squid proxy works as a http blocker but does it have any affect on email clients? When I turn on the proxy in the settings of the email using the port (3128) it does not work.

This seems to maybe be an iptables configuration that I might need to do but to be honest iptables confuse me. I have not been able to set up a transparent proxy due to the iptables. I am running ubuntu 12.04 lts.

Any help/advice is much appreciated. My acl setting is...

acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 465         #ssmtp
acl Safe_ports port 585         #imap4ssl
acl Safe_ports port 993         #imaps
acl Safe_ports port 995         #sslpop
acl Safe_ports port 110         #pop3
acl Safe_ports port 143         #imap
acl Safe_ports port 25          #smtp

acl Connect method Connect


Am I going about this wrong? Thanks again everyone. ](*,)

---

### Post by SeijiSensei on 2012-12-18
> **lestertorres said:**
> Am I going about this wrong?

Yes.  Squid is designed to proxy HTTP requests.  E-mail doesn't use any of that.  Your clients have to have connections to the server's SMTP or Mail Submission port and an IMAP or POP3 connection as well.

You don't tell us what kind of mail server you're trying to reach.  If it uses a webmail service like Hotmail or GMail, you can install a [plug-in]("http://webmail.mozdev.org/") for Thunderbird that will connect to them.  Otherwise you have to configure TBird with the server's SMTP and POP or IMAP connections.

To do this you'll need to deal with iptables and figure out [how to masquerade traffic]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29").  You will also need to edit /etc/sysctl.conf and uncomment net.ipv4.ip_forward=1 as described in that article.

If the email server sits behind the proxy machine in the same subnet as the clients, then you don't need to worry about masquerading.  Just point to the server when you run the Thunderbird configuration.  Somehow I suspect, though, that the email server is upstream from your clients.

---

### Post by lestertorres on 2012-12-18
Thanks for the reply Seiji...

The mail server I am trying to reach out is webmail. It can use either a POP3 or IMAP. Our incoming/outgoing mail sever is:

mail.xxx.net

I also have also uncommented net.ipv4.ip_forward=1 in the /etc/sysctl.conf file.When I use Tbird for the mail clients if I go to preferences, advanced, connection > settings, and put no proxy, Tbird works. If I put in the manual proxy configuration it will just stay idle and never make a connection to the mail server. I guess it is because squid does not respond to the mail server.

---

### Post by SeijiSensei on 2012-12-18
As I said, you do not want to use the proxy for this at all.  The mail clients will talk directly to the remote server.

Why do you want them to use the proxy?  What problem are you trying to solve by doing so?

---

### Post by lestertorres on 2012-12-18
This is obviously for my job and my boss wants me to block all sites and create a white list (which I have already) and we use linux terminals and some windows machines. I need the users to be able to use their emails because it is very important that they do but I also need to make sure that all sites are being blocked. That is why I am making them use the proxy. Should I approach the email in a different way? I have about 100-150 users on the network, they also use virtual machines as well and I want to make sure that when I put the proxy to the server it does not interfere with any internet connection.

---

### Post by SeijiSensei on 2012-12-18
Well they are not going to be using their email clients to visit web sites, so if that's the issue, it's already solved.

You could restrict their ability to connect to other mail servers with a couple of iptables rules:

```

/sbin/iptables -A INPUT -p tcp -d ip.addr.of.mailserver --dport 25 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -d ip.addr.of.mailserver --dport 143 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 25  -j REJECT
/sbin/iptables -A INPUT -p tcp --dport 143 -j REJECT

```

This blocks connections to other machines SMTP and IMAP ports except for ip.addr.of.mailserver.  If you're using encrypted connections like TLS, or the alternative mail submission port, you'd need to change the port numbers above.  

This begs the more general question of where people are allowed to go in general.  Unless you specify the destination servers and ports allowed, your users can probably go just about anywhere.  To control that, you'd need a bunch of specific ACCEPT rules like those above for the permitted servers and services and a default iptables policy of DENY to block everything else.

Oh, and what about HTTPS?  I presume you allow connections to remote TCP port 443, right?  Managing SSL connections with Squid is [possible]("http://wiki.squid-cache.org/Features/SslBump") but requires a lot of client-side configuration including installing self-signed SSL certificates in every browser.

You all need to develop a comprehensive security policy.  Sit down with your boss and anyone else who should be involved and identify precisely what it is that people need to use the Internet for.  Develop a set of iptables rules to embody the policy.  Trying to do things like this on an ad-hoc basis generally leads to problems.

---

### Post by lestertorres on 2012-12-18
Ok its making sense what you are telling me. So in the preferences for Tbir or Evo I do not use the proxy but what happens when I do it through a Windows machine for Outlook? I am attempting to do so on my lap top that I have connected to a switch that is connected to eth1. For some reason the icon on my windows machine shows no internet access, although I do have connection online through the proxy.I am sure that by the end of this I am going to be a squid master lol

---

