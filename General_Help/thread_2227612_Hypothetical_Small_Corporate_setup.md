---
title: "Hypothetical Small Corporate setup"
date: 2014-06-03
forum: General Help
---

### Post by newb85 on 2014-06-03
So I've been toying around with a few networked VMs to set up what I would consider an ideal setup for a very small company:

[LIST]
[*]Fixed local IPs - this is trivial using /etc/network/interfaces
[*]Packages downloaded through a central server to save on bandwidth/cost - this I have successfully done this using squid-deb-proxy.
[*]Unified accounts across all machines - this I'm not sure how to do.  It seems the app sync-accounts was designed to accomplish this, but it also seems to have been pulled from the repos.  Besides, I can find essentially no information on how to use it, aside from the man page.  Any suggestions here would be appreciated.
[*]Also, I would love to hear other thoughts on overall setup.
[/LIST]

---

### Post by SeijiSensei on 2014-06-03
In many small companies the fact that you're not using Windows will befuddle some users entirely.

As for authentication, you need to use a protocol like NIS or LDAP with a central server on which all the accounts are stored.  Traditionally Unix systems used NIS for authentication with the users' home directories on an NFS server.

Another option is to centralize everything and use the PCs as terminals.  Take a look at the [Linux Terminal Server Project]("http://www.ltsp.org/") for details.

---

### Post by Tadaen_Sylvermane on 2014-06-03
+1 for LTSP. I will mention though that I couldn't get it to work on Ubuntu. Worked great with a Debian wheezy server though.

---

