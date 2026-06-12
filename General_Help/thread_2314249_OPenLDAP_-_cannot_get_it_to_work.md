---
title: "OPenLDAP - cannot get it to work"
date: 2016-02-19
forum: General Help
---

### Post by DinghySailor on 2016-02-19
I have installed OpenLDAP on my 12.02 server. From that PC, I set up the host address etc., and have scanned the forums for advice, but if I try to add to the directory using the LDAP Administration tool, I get an error saying "Invalid DN syntax". I have tried ldapsearch, which responds with[INDENT][I]# extended LDIF
#
# LDAPv3
# base <> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object[/I]
[/INDENT]

I tried installing phpldapadmin, but I only get a Page 404 error.

My apologies if I'm being dense, but I have been unable to find a solution, and this is about my 4th attempt to get this going. All I want form it, is to be able to have names, addresses and emails.

Thank you for your help.

Kind Regards,

---

### Post by DinghySailor on 2016-03-01
Just to add a comment, when I use the LDAP Administration tool, it does pick up the LDAP server, but cannot add or do anything to it.

Could this be file permissions, in which case, what do I need to change, and to what?

If not, any ideas, or is there any other debug that would help?

Many thanks,

---

