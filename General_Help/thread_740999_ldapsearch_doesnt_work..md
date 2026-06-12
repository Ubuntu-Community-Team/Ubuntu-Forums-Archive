---
title: "ldapsearch doesnt work."
date: 2008-03-31
forum: General Help
---

### Post by invincible_soul on 2008-03-31
Hii All,

I am new to this forum so i dont know where to post. sory for that.


I am using openldap v2.3 on redhat el4. When i run ldapsearch it returns all the entries. The command runs successfully. But when I run the ldapsearch with following filter option it doesnt work and immediately returns to the shell.

ldapsearch uidNumber>=2000

I've started slapd in debug mode so that i can trace for the errors. When i run this command there is no error shown there i.e. err=0.

Some similar search results are as follows :

$ ldapsearch -x -L "(&(gidNumber=102)(uidNumber>=2000))"
version: 1

#
# LDAPv3
# base <> with scope subtree
# filter: (&(gidNumber=102)(uidNumber>=2000))
# requesting: ALL
#

# search result

# numResponses: 1



$ ldapsearch -x -L "(&(gidNumber=102)(uidNumber>2000))"
version: 1

#
# LDAPv3
# base <> with scope subtree
# filter: (&(gidNumber=102)(uidNumber>2000))
# requesting: ALL
#

ldapsearch: ldap_search_ext: Bad search filter (-7)



I think ldap server is accepting only '=' searchfilter. It is not able to take '>' , '>=' etc. type of search filters.

But y so ?

can anybody please help me.

---

### Post by smcleish on 2008-04-08
I'm something of an LDAP novice myself - it's one of those things I tend to get working when I need it and then forget.

The last search appears to be invalid (should be >= not >). (See section 3 of RFC 4515, handily summarised and made intelligible [here]("http://www.zytrax.com/books/ldap/apa/search.html").

Are you sure that the search should return something? I'd imagine so, but the search results are consistent with no uidNumber values over 2000.

Other than that, perhaps you should try posting in an openldap forum or mailing list.

Cheers,
Simon

---

