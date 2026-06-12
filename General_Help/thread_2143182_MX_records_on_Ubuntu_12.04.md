---
title: "MX records on Ubuntu 12.04"
date: 2013-05-08
forum: General Help
---

### Post by me01273 on 2013-05-08
Hi,

I am moving web hosts from a managed service to a dedicated server which I manage myself.
I have got my lamp stack up and running fine, but I am at a complete loss about email.

We are using Google Apps for our email and in our current host, I set up MX records in cPanel.
I have Googled, but cannot seem to find really what I'm after.

How do I set up MX record redirection on an Ubuntu server? I'm not after Postfix or SMTP redirection.

Many thanks
David

---

### Post by SeijiSensei on 2013-05-08
Where are your DNS records hosted now?  It sounds like they might be hosted by the company you are leaving.  If not, then just leave your MX records the way they are now so your mail will continue to be sent to Google.  

If you need to move your DNS records entirely, then I suggest you visit your registrar's site to see if they can be hosted there for free or for a nominal fee.  While you could host your own DNS on your new server, that is one of the more complex services to configure.  It's often much easier to use your registrar's web interface to manage your records.  Letting someone else host your DNS also exempts you from the need to provide a second name server as Internet [standards]("http://tools.ietf.org/html/rfc1912") (see section 2.8) require.   

I suggest taking a look at your complete domain record, by running a whois query on your domain name.  You will need to install the whois client with "sudo apt-get install whois", then just run the command "whois yourdomain.name" to see your records.  You'll see the name of your registrar, the "contacts" for your domain, and the names of your DNS servers.

Down the road you might decide to move both mail and DNS from your current provider(s) to your new server.  Then you would need to change your MX records to point to your server's public IP address.   If you move DNS, one of your NS records will also need to point to this address, but you will still need to have a public secondary somewhere else.  Your registrar might be able to offer this.  I meet the standard by having two VMs at [Linode]("http://www.linode.com/") (one on each US coast), so I run my own primary and secondary nameservers.

One other thing.  Make sure your server's public IP address has correct reverse DNS resolution set up.  Not only is this the correct policy to follow generally, but if you ever start sending mail, having an unmatched host name and IP address will cause problems.  Many mail servers are rightly suspicious if a sending server announces itself with a name different from that returned by a reverse lookup on the IP address.  Here's an example of a correct configuration from one of Google's outbound servers:

```

$ host mail-ia0-f178.google.com
mail-ia0-f178.google.com has address 209.85.210.178
$ host -t ptr 209.85.210.178
178.210.85.209.in-addr.arpa domain name pointer mail-ia0-f178.google.com.

```

The A record for the host name mail-ia0-f178.google.com points to the address 209.85.210.178, and the PTR record for that address points to the host name.  Your VM provider should be able to set this up for you once you decide on what the name of the machine will be.  At Linode, I can do this myself using the web interface.

---

