---
title: "Help configuring OpenLDAP on Ubuntu Server 12.04"
date: 2013-01-16
forum: General Help
---

### Post by andykohsamui on 2013-01-16
Hi all,

First post on the forum here after trawling over the web for information that will help me with my problem.

I work in a small school and I have a Ubuntu server (which is great!) for file, print and intranet server duties. Our email accounts are hosted with our ISP which works just fine, but I have been asked to implement a shared address book. Having done my research, I chose to use OpenLDAP on the Ubuntu server for this duty, however, this is where the problems start.

Firstly, most of the documentation for OpenLDAP (including on the actual developer's site) refers to slapd.conf which is deprecated, you now use the 'ldapadd' commands. I've found a good few sites that explain how to add schemas to your LDAP server, but I'm struggling with the authentication part.

When I go to add a schema to a fresh install of OpenLDAP, it gives me an authentication error (ldap error 53 no global superior knowledge). Looking around, people state that this is because I have incorrectly named the dn for my LDAP server in the configuration (when using dpkg-reconfigure on slapd you can set all of this up).

In my hosts file I can see my server name is as I've set it, but it's a simple name with no .net or whatever suffix - what should I use as my FQDN when configuring slapd?

It all seems like such hard work for a shared address book, but it's what the managers want so I have to at least try and provide it for them!

Any help by people who have experience with LDAP and how to set it up would be greatly appreciated! This site has helped me on many other issues in the past!

Cheers,

Andy

---

